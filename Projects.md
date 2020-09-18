# 구남현 (Namhyun, Gu)

## 프로젝트

프로젝트 별 링크를 통해 세부 정보를 확인할 수 있습니다

## 목차

  - [Android](#android)
  - [Flutter](#flutter)
  - [Go](#go)
  - [Node.js](#nodejs)

### Android

- [geo-key](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/geo-key.md)  
  
  위치를 기반으로 키를 저장하고, 저장한 키를 관리할 수 있는 애플리케이션입니다.  
  
  - 언어 : **Kotlin**  
  - 기술 : **Dagger Hilt**, **Coroutine**, Firebase, Naver Map  
  - 아키텍처 : **MVVM, Clean Architecture**  

- [intent-contract](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/intent-contract.md)

  타입에 안전한 Intent 사용을 위해 개발된 라이브러리입니다.

  - 언어 : **Kotlin**
  - 기술 : **Annotation Processor**

- [mapp](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/mapp.md)  

  임베디드 소프웨어 수업의 팀 프로젝트로 진행하였으며,  
  셀럽, 프로그램에 따른 맛집을 소개하고, 리뷰를 작성할 수 있는 애플리케이션입니다.  

  이 프로젝트에서 셀럽, 프로그램을 **자동완성을 포함한 검색 기능**을 구현하였으며,  
  즐겨찾기한 맛집에 **새 리뷰가 작성될 때 알림을 전달하는 기능**과  
  메인 화면 내 셀럽, 프로그램 리스트, 알림 리스트를 담당하여 구현하였습니다.

  - 언어 : **Kotlin**
  - 기술 : **Koin (DI), Coroutine**, Room database, Firebase, Naver Map
  - 아키텍처 : **MVVM**

- [SceneSpotInSeoul](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/SceneSpotInSeoul.md)  

  서울시 앱공모전 2018에 참여한 프로젝트로 드라마, 영화 등 미디어의 촬영지를 제공하고,  
  촬영장면과 동일한 사진을 찍을 수 도와주는 애플리케이션입니다.

  이 프로젝트에서 **미디어, 장소, 장면별 리스트를 제공하는 메인 화면**을 구현하였으며,  
  앱 내 컨텐츠를 검색할 수 있는 **자동완성을 포함한 검색 기능**과  
  **앱 내의 내부 데이터베이스와 서버 데이터베이스를 동기화하는 기능**을 구현하였습니다.  
  그리고, **서버와 데이터 관리 페이지 구현**을 담당하였습니다.  

  - 언어 : Java, Kotlin (Android) / Javascript (Server, 데이터 관리 페이지)
  - 기술
    - Android : **Android Architecture Component**, Room database
    - Server : **Serverless framework, AWS lambda, AWS dynamoDB**
    - 데이터 관리 페이지 : **React**

- [BitcoinSimulator](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/BitcoinSimulator.md)

  Bithumb의 비트코인 시세 API를 비트코인 투자를 시뮬레이션 해볼 수 있는 애플리케이션입니다.  

  - 언어 : **Kotlin**
  - 기술 : **Android Architecture Component, RxJava**, Realm Database
  - 아키텍처 : **MVVM**

- [MealViewer](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/MealViewer.md)

  Neis 서비스의 학교 급식 정보를 제공하는 애플리케이션입니다.  
  플레이스토어에 처음 게시해본 애플리케이션이며, 5,000명정도의 다운로드 수, 4.4점의 평점을 기록하였습니다.

  - 언어 : **Java**
  - 기술 : **Dagger 2**, **RxJava**, Realm Database
  - 아키텍처 : **MVP**
  
### Flutter

- [fill-memo](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/fill-memo.md)
  
  졸업 프로젝트로 진행한 프로젝트였으며,
  서식 있는 텍스트, 마크다운을 통한 메모 작성을 지원하고, 여러 기기에서 연동해 이용할 수 있는 웹/앱입니다.

  이 프로젝트에서 **메인 화면과 폴더 기능**을 구현하였으며,  
  **서식 있는 텍스트 메모 기능**, **세션 공유를 위한 인증 서버**,  
  개발한 **앱을 웹으로 마이그레이션**하는 작업을 담당하였습니다.

  - 언어 : **Dart** (Client) / **Go** (Auth Server)
  - 기술 : Firebase, **gRPC** (Client) / **gRPC**, Redis (Auth Server)
  - 아키텍처 : **BLoC** (Client)

- [flutter_rich_text_editor](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/flutter_rich_text_editor.md)
  
  Flutter에서 이용 가능한 서식 있는 텍스트 에디터를 제공하는 라이브러리입니다.

  졸업 프로젝트때 개발했던 에디터를 라이브러리로 분리한 프로젝트입니다.

  - 언어 : **Dart**

- [preference_helper](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/preference_helper.md)
  
  Flutter를 BLoC 아키텍처 패턴으로 개발할 때 `SharedPreferences`를 쉽게 이용할 수 있도록 만든 라이브러리입니다.

  라이브러리에 `SharedPreferences`를 다루는 BLoC이 구현되어 있으며 이 BLoC를 통해 추가, 업데이트가 가능하고,  
  변경될 때마다 업데이트 된 시간과 `SharedPreferences`의 내용이 State로 전달되어 이용할 수 있습니다.

  - 언어 : **Dart**

### Go

- [key-letter](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/key-letter.md)
  
  졸업 프로젝트에서 개발한 인증 서버를 다양한 경우에 이용할 수 있도록 만든 프로젝트입니다.

  - 기술 : **gRPC**, Redis

### Node.js

- [repo-watcher](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/repo-watcher.md)
  
  리포지토리에 업데이트 된 커밋 메시지를 메일을 통해 받을 수 있는 서비스입니다.

  - 언어 : **Typescript**
  - 기술 : **Github Actions**, nodemailer

- [contest-crawler-bot](https://github.com/namhyun-gu/namhyun-gu/blob/master/projects/contest-crawler-bot.md)
  
  공모전 정보를 크롤링하고 업데이트 된 공모전 정보를 텔레그램 봇을 통해 알려주는 서비스입니다.

  - 언어 : **Javascript**
  - 기술 : **Express**, **Telegram Bot API**, Firebase
