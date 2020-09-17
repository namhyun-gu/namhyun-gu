# flutter_rich_text_editor

Flutter에서 이용 가능한 서식 있는 텍스트 에디터를 제공하는 라이브러리입니다.

## 바로가기

- [Github](https://github.com/namhyun-gu/flutter_rich_text_editor)

## 프로젝트 정보

### 언어

- Dart

### 기술

- Flutter

### 노트

이 프로젝트는 졸업 프로젝트였던 [fill-memo](https://github.com/smu-gp/fill-memo)에서 개발 후 라이브러리 형태로 분리한 프로젝트입니다.

Flutter의 `TextField`에 라이브러리에 포함된 `SpannableTextEditingController`를 추가하여 이용할 수 있으며
필요한 경우 기본으로 제공되는 `StyleToolbar` 위젯을 활용할 수 있습니다.

제공하는 SpannableTextEditingController는 다음 기능을 이용할 수 있습니다.

- 텍스트 스타일 변경
  - 굵게
  - 기울임꼴
  - 취소선
  - 밑줄
  - 색상
- 실행취소 & 재실행

- SpannableTextEditingController 예제

```dart
SpannableTextEditingController controller = SpannableTextEditingController();

TextField(
  controller: controller,
  keyboardType: TextInputType.multiline,
  maxLines: null,
  decoration: InputDecoration(
    border: InputBorder.none,
    focusedBorder: InputBorder.none,
    filled: false,
  ),
)
```

- StyleToolbar 예제

```dart
SpannableTextEditingController controller = SpannableTextEditingController();

StyleToolbar(
  controller: controller,
)
```

## 스크린샷

![example](https://github.com/smu-gp/fill-memo/raw/master/art/rich-text-editor_1.png)
