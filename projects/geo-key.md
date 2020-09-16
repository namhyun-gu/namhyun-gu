# [geo-key](https://github.com/namhyun-gu/geo-key)

> 위치를 기반으로 저장한 키들을 확인하고 관리하는 애플리케이션입니다.

### 사용한 언어

- Kotlin

### 사용한 기술

- **Dagger Hilt**
- **Coroutine**
- Retrofit
- Moshi
- Firebase
  - Cloud Firestore
  - Firebase Auth
- Naver Map

### 아키텍처

- **MVVM, Clean Architecture**

### 노트

이 프로젝트는 [google/iosched](https://github.com/google/iosched)의 Clean Architecture와 MVVM 패턴, 그리고 Coroutine를 이용하여 개발한 프로젝트입니다.

UseCase들은 지속적으로 데이터를 전달하는 경우와 그렇지 않은 경우에 따라 구분한 FlowUseCase와 UseCase를 사용하며, Dagger Hilt를 통해 ViewModel에 주입하여 서비스의 기능들을 구현합니다.

현재 Jetpack Navigation을 통해 Single Activity로 전환하고 있으며,
추후 Jetpack Compose가 안정적으로 업데이트 될 떄 Jetpack compose로의 전환을 계획하고 있습니다.

<details>
<summary>UseCase 예시</summary>

```kotlin
class GetAddressUseCase @Inject constructor(
    private val geocodingService: GeocodingService,
    @IoDispatcher ioDispatcher: CoroutineDispatcher
) : UseCase<LocationModel, String>(ioDispatcher) {
    override suspend fun execute(parameters: LocationModel): String {
        val coords = "${parameters.lon},${parameters.lat}"
        val address = geocodingService.reverseGeocode(
            BuildConfig.NCP_CLIENT_ID,
            BuildConfig.NCP_CLIENT_SECRET,
            coords
        ).getAddress()
        return address ?: ""
    }
}
```

</details>

<details>
<summary>FlowUseCase 예시</summary>

```kotlin
@ExperimentalCoroutinesApi
class GetLocationsUseCase @Inject constructor(
    private val locationDataSource: LocationDataSource,
    @MainDispatcher mainDispatcher: CoroutineDispatcher
) : FlowUseCase<Unit, LocationModel>(mainDispatcher) {
    override fun execute(parameters: Unit): Flow<Result<LocationModel>> {
        return flow {
            emit(Result.Success(locationDataSource.getLastLocation()))
            locationDataSource.getLocationUpdates().collect {
                emit(Result.Success(it))
            }
        }
    }
}
```

</details>

<details>
<summary>ViewModel 에시</summary>

```kotlin
@ExperimentalCoroutinesApi
class MainViewModel @ViewModelInject constructor(
    getKeysUseCase: GetKeysUseCase,
    getLocationsUseCase: GetLocationsUseCase,
    getAddressUseCase: GetAddressUseCase
) : ViewModel() {
    val keys = liveData {
        emit(null)
        getKeysUseCase(Unit).collect {
            if (it.succeeded) {
                emit(it.data)
            }
        }
    }

    val location = liveData {
        emit(null)
        getLocationsUseCase(Unit).collect { locationResult ->
            when (locationResult) {
                is Result.Success -> {
                    when (val addressResult = getAddressUseCase(locationResult.data)) {
                        is Result.Success -> {
                            val (_, lat, lon) = locationResult.data
                            emit(LocationModel(addressResult.data, lat, lon))
                        }
                        is Result.Error -> {
                            Timber.e(addressResult.exception)
                        }
                    }
                }
                is Result.Error -> {
                    Timber.e(locationResult.exception)
                }
            }
        }
    }

}

```

</details>

### 스크린샷

<!-- TODO -->
