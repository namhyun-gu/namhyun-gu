# SceneSpotInSeoul

서울시 앱공모전 2018에 참여한 프로젝트로 드라마, 영화 등 미디어의 촬영지를 제공하고 촬영 장면과 동일한 사진을 찍을 수 있도록 도와주는 애플리케이션입니다.

## 바로가기

- [Github - Android](https://github.com/three-s/SceneSpotInSeoul)
- [Github - Server](https://github.com/three-s/SceneSpotInSeoul-Lambda)
- [Github - Database Explorer](https://github.com/three-s/SceneSpotInSeoul-Database-Explorer)

## 프로젝트 정보

### 언어

- Android : Java, Kotlin
- Server : Javascript
- 데이터 관리 페이지 : Javascript

### 기술

- Android
  - Android Architecture Component (AAC)
  - Room database
  - Retrofit
  - Naver Map

- Server
  - Serverless framework
  - AWS lambda
  - AWS dynamoDB

- 데이터 관리 페이지
  - React
  - Axios

## 맡은 부분

- 메인 화면 (미디어, 장소, 장면별 리스트)
- 앱 - 서버 데이터베이스 동기화 기능
- DynamoDB 사용을 위한 CRUD Serverless lambda 서버
- 앱에 사용될 데이터를 관리하기 위한 웹페이지

## 노트

이 프로젝트에서는 프로젝트 개발 중 내부 DB가 아닌 외부 DB가 필요함에 따라 AWS의 lambda, dynamoDB를 처음으로 사용한 프로젝트입니다.
Firebase를 이용하는 것과 달리 동기화 부분을 스스로 처리해야 되는 점에서 개발에 까다로웠던 프로젝트였습니다.

서버는 빠른 개발을 위해 [Serverless framework](https://www.serverless.com/)를 사용하여 개발하였습니다.

앱과 서버 간 데이터 동기화는 서버의 특정 테이블 변경 시간대를 기록하고, 애플리케이션에 저장된 테이블 시간대와 비교하여 특정 테이블만 업데이트하는 식의 동기화 기능을 구현했습니다. 동기화 기능은 AAC의 Worker를 사용하여 개발했습니다.

- [SyncDatabaseWorker.kt](https://github.com/three-s/SceneSpotInSeoul/blob/master/app/src/main/java/com/threes/scenespotinseoul/workers/SyncDatabaseWorker.kt)

```kotlin
class SyncDatabaseWorker : Worker() {

    companion object {
        private val TAG = SyncDatabaseWorker::class.java.simpleName
    }

    override fun doWork(): Result {
        val db = AppDatabase.getInstance(applicationContext)
        val retrofit = Retrofit.Builder()
            .baseUrl(REMOTE_ENDPOINT_URL)
            .addConverterFactory(GsonConverterFactory.create())
            .build()

        val service = retrofit.create(RemoteDatabaseService::class.java)
        val infoResponse = service.loadInfo().execute()
        try {
            var updatedTables = 0
            infoResponse.body()?.forEach {
                val localInfo = db.dataInfoDao().load(it.name)
                if (localInfo == null || isOutOfDate(localInfo, it)) {
                    Log.d(TAG, "${it.name} is out-of-date. Proceed Sync.")
                    when (it.name) {
                        LOCATION_TABLE -> {
                            val locationsResponse = service.loadLocations().execute()
                            val locationWrappers = locationsResponse.body()
                            if (locationWrappers != null && locationWrappers.isNotEmpty()) {
                                writeLocations(db, locationWrappers)
                                writeDataInfo(db, it)
                            }
                        }
                        MEDIA_TABLE -> {
                            val mediaResponse = service.loadMedia().execute()
                            val mediaWrappers = mediaResponse.body()
                            if (mediaWrappers != null && mediaWrappers.isNotEmpty()) {
                                writeMedia(db, mediaWrappers)
                                writeDataInfo(db, it)
                            }
                        }
                        SCENE_TABLE -> {
                            val scenesResponse = service.loadScenes().execute()
                            val sceneWrappers = scenesResponse.body()
                            if (sceneWrappers != null && sceneWrappers.isNotEmpty()) {
                                writeScenes(db, sceneWrappers)
                                writeDataInfo(db, it)
                            }
                        }
                    }
                    updatedTables++
                } else {
                    Log.d(TAG, "${it.name} is up-to-date. Passed Sync.")
                }
            }
            if (updatedTables > 0) {
                pruneTags(db)
            }
            return Worker.Result.SUCCESS
        } catch (ex: IOException) {
            return Worker.Result.FAILURE
        }
    }

    // ...
}
```