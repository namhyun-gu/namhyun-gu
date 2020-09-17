# intent-contract

타입에 안전한 Intent 사용을 위한 라이브러리입니다.

## 바로가기

- [Github](https://github.com/namhyun-gu/intent-contract)
- [Bintray](https://bintray.com/namhyun-gu/intentcontract/intentcontract-compiler/0.1.2)

## 프로젝트 정보

### 언어

- Kotlin

### 기술

- **Annotation Processor**
- KotlinPoet

## 노트

이 프로젝트는 안드로이드를 개발할 때 Intent를 통해 다른 Activity에 값을 전달할 때 타입에 맞지 않게 데이터가 전달되어 발생하는 오류를 줄여보고자 Annotation Processor를 처음으로 배워 적용해본 라이브러리 프로젝트입니다.

이 라이브러리는 다음 과정을 통해 Intent를 이용할 수 있습니다.

1.  Activity에 `@IntentTarget` Annotation을 추가합니다.
2.  데이터를 전달 받을 변수에 `@Extra` Annotation을 추가하고, 꼭 필요한 데이터가 아니라면 `@Optional` Annotation을 추가합니다.
3.  그리고, onCreate에서 `IntentContracts.contract(context)` 를 통해 Activity에 데이터가 전달될 때 변수에 값을 바인딩합니다.
4.  1, 2의 과정을 통해 생성된 `IntentTargets` 클래스의 메소드를 이용하여 Intent을 생성하고 이용합니다.

```kotlin
@IntentTarget
class SecondActivity : AppCompatActivity() {

    @Extra
    var test: String = "Hello"

    @Optional
    @Extra
    var optionalTest: String = "World"

    override fun onCreate(savedInstanceState: Bundle?) {
      // ...
      IntentContracts.contact(this)
    }

    // ...
}
```

```kotlin
val intent: Intent = IntentTargets.secondActivity(this, test="Test", optionalTest=null)
```
