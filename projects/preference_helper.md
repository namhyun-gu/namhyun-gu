# preference_helper

> Flutter를 BLoC 아키텍처 패턴으로 개발할 때 SharedPreferences를 쉽게 이용할 수 있도록 만든 라이브러리입니다.

### 바로가기

- [Github](https://github.com/namhyun-gu/preference-helper)
- [Pub.dev](https://pub.dev/packages/preference_helper)

### 사용한 언어

- Dart

### 사용한 기술

- Flutter
- BLoC

### 노트

이 프로젝트는 졸업 프로젝트였던 [fill-memo](https://github.com/smu-gp/fill-memo)에서 BLoC로 개발을 할 때 SharedPreferences를 조금이나마 편하게 만들어보고자 개발하게된 라이브러리입니다.

이 라이브러리에는 `PreferenceBloc` 클래스를 포함하고 있으며 `SharedPreferences`의 데이터 읽기/변경에 대한 기능과 `SharedPreferences`가 변경될 때마다 `PreferenceState`를 통해 갱신된 `Preference` 정보와 업데이트된 시간 정보를 가져올 수 있습니다.
