# 구남현

- Github : https://github.com/namhyun-gu
- 이메일 : mnhan0403@gmail.com

## 2021

### [brick](https://github.com/namhyun-gu/brick)

안드로이드 개발에 주로 사용되는 라이브러리들을 카테고리 별로 미리 구성하여 명령어를 통해 최신 버전의 라이브러리 구성을 도와주는 CLI 애플리케이션입니다.

- 2021.03 ~
- 기술 : Go / Github API
- Go 언어와 CLI 개발을 도와주는 Cobra 라이브러리로 개발하였습니다.
- Github에 올린 구성 파일들을 다운로드 하기 위해 Github API를 활용하였습니다.
- 여러 Repository에 저장 된 구성 파일에 접근할 수 있도록 Scoop 서비스의 Bucket 개념을 적용했습니다.

## 2020

### [key-map](https://github.com/namhyun-gu/key-map)

위치를 기반으로 키를 저장하고, 저장한 키를 관리할 수 있는 애플리케이션입니다.

- 2020.06 ~ 2021.02
- 기술 : Kotlin / Dagger Hilt / Coroutines / Firebase / Naver Map
- DI를 적용하기 위해 Dagger Hilt를 이용하였습니다.
- 아키텍처로 MVVM을 적용하였습니다.
- 비동기 작업을 처리하기 위해 Koltin Coroutines을 이용하였습니다.
- 데이터베이스로 실시간 데이터베이스를 제공하는 Firebase Firestore를 이용하였습니다.
- Naver의 Reverse Gecoding API를 이용할 떄 Cronet 라이브러리를 사용했습니다.
- 비슷한 위치끼리 묶은 키 목록과 나머지 목록을 한 리스트에 표시하기 위해 Epoxy를 이용하였습니다.
- CI를 구축하기 위해 Github Actions을 이용하였으며 Firebase App Distribution으로 배포합니다.

### [JetCard](https://github.com/namhyun-gu/JetCard)

Jetpack Compose를 이용하여 개발한 플래시 카드 애플리케이션입니다.

- 2020.11
- 기술 : Kotlin / Jetpack Compose / Dagger Hilt / Coroutines / Room
- DI를 적용하기 위해 Dagger Hilt를 이용하였습니다.
- 아키텍처로 MVVM을 적용하였습니다.
- 데이터베이스 작업에서의 비동기 작업을 처리하기 위해 Kotlin Coroutines을 이용하였습니다.
- 플래시 카드 정보를 저장하기 위해 Room Database를 사용하였습니다.

## 2019

### [mapp](https://github.com/team-mapp/mapp)

셀럽이나 TV 프로그램에 방영된 맛집을 소개하고 리뷰를 작성할 수 있는 애플리케이션입니다.

- 2019.10 - 2019.12
- 기술 : Kotlin / Koin (DI) / Kotlin Coroutines / Room database / Firebase / Naver Map
- 안드로이드 개발 4명으로 진행한 팀 프로젝트입니다.
- 이 프로젝트에서 다음 부분을 담당하였습니다.
  - 구글 로그인 기능
  - 메인 화면 내 셀럽, 프로그램 리스트, 알림 리스트
  - 자동완성을 포함한 앱 내 셀럽, 프로그램, 맛집 검색 기능
  - 관심 있는 맛집에 대한 새 리뷰 작성 알림 (FCM)
  - 새 리뷰 작성 알림을 위한 Firebase Functions 함수 작성
- DI를 적용하기 위해 Koin을 이용하였습니다.
- 아키텍처로 MVVM을 적용하였습니다.
- 데이터베이스로 실시간 데이터베이스를 제공하는 Firebase Firestore를 이용하였습니다.
- 로그인 기능을 구현하기 위해 Firebase Authentication을 이용하였습니다.
- 데이터베이스는 Repository 패턴으로 작성된 Repository들로 이용합니다.
- 알림 리스트를 구현하기 위해 수신 된 알림을 Room 데이터베이스에 저장하여 실시간으로 표시합니다.
- 리스트와 알림 내 이미지를 제공하기 위해 Glide를 사용하였습니다.
- Custom View를 이용하여 프로필과 리스트 아이템 뷰를 재사용했습니다.
- 리스트 아이템마다의 배경 색을 Palette를 사용하여 이미지에서 색상을 추출했습니다.

### [flutter_rich_text_editor](https://github.com/namhyun-gu/flutter_rich_text_editor)

Flutter에서 서식 있는 텍스트 에디터를 사용하기 위해 개발한 라이브러리입니다.

- 2019.06 ~ 2019.09
- 기술 : Dart / Flutter
- [fill-memo](#fill-memo) 프로젝트에 사용되는 서식 있는 텍스트 에디터를 라이브러리로 분리하였습니다.
- Flutter에 포함된 `TextField`에 라이브러리가 제공하는 `SpannableTextEditingController`만 추가하여 기능을 추가할 수 있습니다.
- 글자마다의 스타일을 지정하기 위해 비트마스킹을 이용하였습니다.
  - 글자 색을 표현하기 위해 RGB 각각 8비트를 사용합니다.
  - 굵기, 기울임 등의 스타일을 지정하기 위해 5비트를 사용합니다.
- 작성 시 텍스트 변경을 계산하기 위해 `diff_match_patch` 라이브러리를 이용하였습니다.

### [fill-memo](https://github.com/smu-gp/fill-memo)

서식 있는 텍스트 및 마크다운으로 메모를 작성할 수 있는 애플리케이션입니다.

- 2019.01 ~ 2019.11
- 기술
  - Client : Dart / Flutter / Firebase / gRPC
  - Server : Go / gRPC / Redis
- 안드로이드 개발 3명, 서버 개발 1명으로 진행한 팀 프로젝트입니다.
- 이 프로젝트에서 다음 부분을 담당하였습니다.
  - 메인 화면 메모 리스트 및 폴더 기능
  - 서식 있는 텍스트 에디터
  - 일회용 코드를 통한 로그인 기능 및 연결 기기 정보를 이용한 2단계 인증
  - 웹 버전 마이그레이션
- 상태 관리를 적용하기 위해 BLoC를 이용하였습니다.
- 데이터베이스로 실시간 데이터베이스를 제공하는 Firebase Firestore를 이용하였습니다.
- 서식 있는 텍스트 에디터를 구현할 때 각 글자 별 스타일을 표현하기 위해 비트마스킹을 사용하였습니다.
- 일회용 코드를 통한 로그인 기능을 구현하기 위해 다음 기술을 적용하였습니다.
  - Go 언어로 작성한 gRPC 서버
  - 일정 시간 동안만 유효한 코드를 제공하기 위해 In-Memory DB인 Redis로 코드 별 Timeout 설정
  - 코드 소유자 - 요청자 간 통신을 제공하기 위해 Redis의 Pub/Sub를 이용
  - 데이터베이스 접근을 위한 세션을 주고 받으며 Custom Token으로 생성한 JWT로 로그인
## 2018

### [SceneSpotInSeoul](https://github.com/three-s/SceneSpotInSeoul)

미디어 촬영지와 장면을 제공하여 장면과 같은 장면의 사진을 찍을 수 있도록 도와주는 애플리케이션입니다.

- 2018.09
- 기술
  - App : Java / Kotlin / Android Architecture Component (AAC) / Room Database
  - Server : Node.js / JavaScript / Serverless framework / AWS lambda / AWS dynamoDB
  - DB 관리 페이지 : JavaScript / React
- 서울시 앱공모전 2018에 공모한 프로젝트입니다.
- 안드로이드 개발 5명으로 진행한 팀 프로젝트입니다.
- 이 프로젝트에서 다음 부분을 담당하였습니다.
  - 메인 화면 내 미디어, 장소, 장면별 리스트
  - 자동완성을 포함한 앱 내 콘텐츠 검색 기능
  - 앱 데이터베이스와 서버 데이터베이스를 동기화하는 기능
  - 서버 및 데이터베이스 관리 페이지 구현
- 앱 내 콘텐츠를 저장하기 위해 Room 데이터베이스를 이용하였습니다.
- 앱 데이터베이스와 서버 데이터베이스를 동기화하기 위해 WorkManager를 이용하였습니다.
- 서버 데이터베이스에 접근하기 위해 Retrofit를 이용하였습니다.

## 2017

### [BitcoinSimulator](https://github.com/namhyun-gu/BitcoinSimulator)

Bithumb의 시세 API를 이용하여 비트코인에 대한 시세를 알아내고 이를 통해 투자를 시뮬레이션하는 애플리케이션입니다.

- 2017.12
- 기술 : Kotlin / Android Architecture Component / RxJava / Realm Database
- Bithumb의 시세 API를 활용하기 위해 Retrofit를 이용하였습니다.
- 아키텍처로 MVVM을 적용하였습니다.
- 비동기 작업을 처리하기 위해 RxJava를 이용하였습니다.
- 코인을 투자한 지갑 정보를 저장하기 위해 Realm를 이용하였습니다.

## 2013

### [MealViewer](https://github.com/namhyun-gu/MealViewer)

Neis 서비스의 학교 급식 정보를 제공하는 애플리케이션입니다.

- 2013.08 ~ 2017.05
- 기술 : Java / Dagger 2 / RxJava / Realm Database
- 5,000여 명이 다운로드하였으며 4.4의 평점을 받았습니다.
- DI를 적용하기 위해 Dagger 2를 이용하였습니다.
- 아키텍처로 MVP를 적용하였습니다.
- 급식 정보를 가져오기 위해 Retrofit를 이용하였습니다.
- 비동기 작업을 처리하기 위해 RxJava를 이용하였습니다.
- 급식 정보를 로컬에 저장하여 캐시로 이용하기 위해 Realm를 이용하였습니다.
- https://play.google.com/store/apps/details?id=com.earlier.yma