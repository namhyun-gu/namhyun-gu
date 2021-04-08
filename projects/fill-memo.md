<h1 align="center">fill-memo</h1>

<p align="center">
졸업 프로젝트로 진행한 프로젝트였으며, 서식 있는 텍스트 및 마크다운을 통한 메모 작성을 지원하며 동기화 가능하고 웹/앱을 지원합니다.
</p>

- [바로가기](#바로가기)
- [프로젝트 정보](#프로젝트-정보)
  - [언어](#언어)
  - [기술](#기술)
  - [아키텍처](#아키텍처)
- [맡은 부분](#맡은-부분)
- [노트](#노트)
- [스크린샷](#스크린샷)

## 바로가기

- [Github - Client](https://github.com/smu-gp/fill-memo)
- [Github - Auth Server](https://github.com/smu-gp/sp-auth-server)

## 프로젝트 정보

### 언어

- Client : Dart
- Auth Server : Go

### 기술

- Client
  - Flutter
  - Firebase (Cloud Firestore, Auth, Crashlystics)
  - gRPC

- Auth Server
  - gRPC
  - Redis

### 아키텍처

- Client : BLoC

## 맡은 부분

- 메인 (메모 리스트)
- 폴더 기능
- 서식 있는 텍스트 메모
- 세션 공유를 위한 인증 서버
- 개발한 앱을 웹으로 마이그레이션

## 노트

이 프로젝트는 졸업 프로젝트로 진행했으며 처음으로 Flutter을 사용하여 애플리케이션을 개발해봤습니다.

프로젝트를 진행하며 서식 있는 텍스트 메모 기능을 구현하는 것이 가장 어려운 과제였으며 기능 구현을 위해
Flutter의 TextField 동작 과정을 소스코드 분석을 통해 알아냈고 다음과 같은 설계로 구현했습니다.

![rich_text_editor](art/fill_memo_rich_text_editor.png)

프로젝트에 세선 공유를 통한 2단계 인증 서버도 구현하였는데 이때 Go언어와, gRPC, Redis를 활용하여 개발했으며
인증 과정은 다음과 같은 방식으로 진행됩니다.

1. 연동을 요청하는 Host가 세션 정보를 서버에 전달합니다. (WaitAuth 요쳥)
2. 세션 정보에 따른 연동을 위한 6자리 코드가 Host에게 전달됩니다. (WaitAuth 응답)
3. 서버는 생성한 6자리 코드로 Redis의 PubSub를 통해 구독합니다.
4. 연동하려는 Guest는 Host에게 확인한 코드와 기기 정보를 서버에게 전달합니다. (Auth)
5. 서버는 Guest의 요청에 따라 해당 코드를 구독하는 Subscriber에 Guest의 기기 정보를 전달합니다.
6. 서버의 Subscriber는 Host에게 Guest의 디바이스 정보를 제공하고 허용할 것인지를 묻습니다
   1. Host가 거절 응답을 서버에 전달하면,
      1. 서버는 응답이 돌아옴에 따라 PubSub 채널을 종료합니다.
      2. 서버는 Guest에게 거절 의사를 전달하고 실패 이유를 '호스트가 거절'로 전달합니다.
   2. Host가 승인 응답을 서버에 전달하면,
      1. 서버는 응답이 돌아옴에 따라 PubSub 채널을 종료합니다.
      2. 서버는 Guest에게 승인되었음을 전달하고, 세션 정보를 전달합니다.

다음은 위 과정에 대해 개발 시 만들었던 시퀀스 다이어그램입니다.

![auth_sequence](art/auth_sequence.png)

## 스크린샷

- Web
  
<img src="art/fill_memo_web.png">

- Rich Text Editor

<p align="center">
    <img src="https://github.com/smu-gp/fill-memo/raw/master/art/rich-text-editor_1.png" width="32%"/>
    <img src="https://github.com/smu-gp/fill-memo/raw/master/art/rich-text-editor_2.png" width="32%"/>
    <img src="https://github.com/smu-gp/fill-memo/raw/master/art/rich-text-editor_3.png" width="32%"/>
</p>

- Markdown

<p align="left">
    <img src="https://github.com/smu-gp/fill-memo/raw/master/art/markdown_1.png" width="32%"/>
    <img src="https://github.com/smu-gp/fill-memo/raw/master/art/markdown_2.png" width="32%"/>
</p>

- Connection

<p align="left">
    <img src="https://github.com/smu-gp/fill-memo/raw/master/art/connection_1.png" width="32%"/>
    <img src="https://github.com/smu-gp/fill-memo/raw/master/art/connection_2.png" width="32%"/>
</p>

<p align="left">
    <img src="https://github.com/smu-gp/fill-memo/raw/master/art/connection_3.png" width="32%"/>
    <img src="https://github.com/smu-gp/fill-memo/raw/master/art/connection_4.png" width="32%"/>
</p>