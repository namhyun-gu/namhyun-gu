# 구남현

이메일 : mnhan0403@gmail.com

## 2021

### [brick](https://github.com/namhyun-gu/brick)

- 2021.03
- 안드로이드 개발에 주로 사용되는 라이브러리들을 카테고리 별로 미리 구성하여 필요한 라이브러리를 명령어를 통해 최신 버전으로 구성할 수 있게 도와주는 CLI 애플리케이션입니다.
  ```bash
  $ ./brick get jetpack:activity jetpack:material --gradle=kotlin
  implementation("androidx.activity:activity-ktx:1.3.0-alpha05")
  implementation("com.google.android.material:material:1.4.0-alpha02")
  ```
- 기술 : Go / Github API

## 2020

### [key-map](https://github.com/namhyun-gu/key-map)

- 2020.06 ~ 2021.02
- 위치를 기반으로 키를 저장하고, 저장한 키를 관리할 수 있는 애플리케이션입니다.
- 기술 : Kotlin / Dagger Hilt / Coroutines / Firebase / Naver Map
- 아키텍처 : MVVM

### [JetCard](https://github.com/namhyun-gu/JetCard)

- 2020.11
- Jetpack Compose를 이용하여 개발한 플래시 카드 애플리케이션입니다.
- 기술 : Kotlin / Jetpack Compose / Dagger Hilt / Coroutines / Room
- 아키텍처 : MVVM

### [repo-watcher](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/repo-watcher.md)

- 2020.08 ~ 2020.10
- 하루 동안 Repository에 업데이트된 커밋 메시지들을 메일을 통해 받을 수 있도록 하는 프로젝트입니다.
- 기술 : Node.js / TypeScript / Github Actions / nodemailer

### [intent-contract](https://github.com/namhyun-gu/intent-contract)

- 2020.06
- 타입에 안전한 `Intent` 사용을 위해 개발한 라이브러리입니다.
- `ButterKnife`에 영감을 받아 만든 라이브러리이며 `@IntentTarget`, `@Extra` Annotation을 코드에 추가하여 다음과 같이 `Intent`를 이용할 수 있게 합니다.
  ```kotlin
  @IntentTarget
  class SecondActivity : AppCompatActivity() {
    @Extra
    var test: String = "Hello"

    override fun onCreate(savedInstanceState: Bundle?) {
      // ...
      IntentContracts.contact(this)
    }
  }

  val intent: Intent = IntentTargets.secondActivity(this, test="Test")
  ```
- 기술 : Kotlin / Annotation Processor / KotlinPoet

## 2019

### [mapp](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/mapp.md)

- 2019.10 - 2019.12
- 임베디드 소프트웨어 수업의 팀 프로젝트로 진행
- 셀럽, 프로그램에 따른 맛집을 소개하고, 리뷰를 작성할 수 있는 애플리케이션입니다.
- 맡은 부분
  - 메인 화면 내 셀럽, 프로그램 리스트 및 알림 리스트
  - 셀럽, 프로그램 내용의 자동완성을 포함한 검색 기능
  - 즐겨찾기한 맛집에 새 리뷰가 작성될 때 알림을 전달하는 기능 (FCM)
- 기술 : Kotlin / Koin (DI) / Kotlin Coroutines / Room database / Firebase / Naver Map
- 아키텍처 : MVVM

### [contest-crawler-bot](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/contest-crawler-bot.md)

- 2019.07
- 공모전 정보를 크롤링 하여 새로 공개된 공모전 정보를 텔레그램 봇을 통해 알려주는 프로젝트입니다.
- 기술 : Node.js / Express / Telegram Bot API / Firebase

### [flutter_rich_text_editor](https://github.com/namhyun-gu/flutter_rich_text_editor)

- 2019.09
- Flutter에서 서식 있는 텍스트 에디터를 이용하기 위해 개발한 라이브러리입니다.
- 구현 방법
  - `TextField` 위젯이 `TextEditingController`라는 컨트롤러에 의해 `TextSpan` 객체로 텍스트를 표현함을 발견하여, `TextEditingController`를 확장한 `SpannableTextEditingController` 구현
  - `SpannableTextEditingController`에는 텍스트와 `SpannbleStyle`이라는 스타일을 저장하는 `SpannbleList`를 가지며, `SpannableStyle`은 하나의 정수를 포함하여 비트 연산을 이용하여 스타일을 표현
  - `SpannbleList`를 통해 `TextSpan`을 객체를 생성할 수 있으며 이때 같은 스타일끼리 그룹을 만들어 하나의 `TextSpan`으로 텍스트를 표현
  - 텍스트의 변경을 감지하기 위해 Google의 `diff_patch_match` 라이브러리를 이용하여 삽입/삭제 여부를 알아내어 `SpannableList`을 확장/축소하여 올바른 `TextSpan` 객체를 만들 수 있도록 함
- 기술 : Dart / Flutter

### [fill-memo](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/fill-memo.md)

- 2019.01 ~ 2019.11
- 졸업 프로젝트로 진행한 프로젝트입니다.
- 서식 있는 텍스트 및 마크다운을 통한 메모 작성을 지원하며 동기화 가능하고 웹/앱을 지원합니다.
- 맡은 부분
  - 메인 화면 내 메모 그리드, 리스트
  - 메모를 분류할 수 있는 폴더 기능
  - [서식 있는 텍스트 에디터](https://github.com/namhyun-gu/flutter_rich_text_editor)
  - 동기화 기능 제공에 있어 세션 공유를 위한 인증 서버
  - 개발된 App을 Web에 호환되도록 마이그레이션
- 기술
  - App, Web : Dart / Flutter / Firebase / gRPC
  - Auth Server : Go / gRPC / Redis
- 아키텍처
  - App, Web : BLoC

## 2018

### [SceneSpotInSeoul](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/SceneSpotInSeoul.md)

- 2018.09
- 서울시 앱공모전 2018에 참여한 프로젝트입니다.
- 드라마, 영화 등 미디어의 촬영지 정보를 제공하고 해당 장면과 동일한 사진을 찍을 수 있도록 도와주는 애플리케이션입니다.
- 맡은 부분
  - 메인 화면 내 미디어, 장소, 장면별 리스트
  - 자동완성을 포함한 앱 내 콘텐츠 검색
  - 앱 내 내부 DB와 서버 DB를 동기화하는 기능
  - 서버 (AWS lambda) 및 DB 관리 페이지 (React) 구현
- 기술
  - App : Java / Kotlin / Android Architecture Component (AAC) / Room Database
  - Server : Node.js / JavaScript / Serverless framework / AWS lambda / AWS dynamoDB
  - DB 관리 페이지 : JavaScript / React

## 2017

### [BitcoinSimulator](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/BitcoinSimulator.md)

- 2017.12
- Bithumb 비트코인 시세 API를 활용하여 비트코인 투자를 시뮬레이션 해볼 수 있는 애플리케이션입니다.
- 기술 : Kotlin / Android Architecture Component / RxJava / Realm Database
- 아키텍처 : MVVM

## 2013

### [MealViewer](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/MealViewer.md)

- 2013.08 ~ 2017.05
- Neis 서비스의 학교 급식 정보를 제공하는 애플리케이션입니다.
- 처음으로 Play Store에 게시한 애플리케이션
- 5,000명 정도의 다운로드 수, 4.4점의 평점 기록
- 기술 : Java / Dagger 2 / RxJava / Realm Database
- 아키텍처 : MVP
- https://play.google.com/store/apps/details?id=com.earlier.yma