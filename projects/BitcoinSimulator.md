# BitcoinSimulator

Bithumb의 비트코인 시세 API를 통해 비트코인 투자를 시뮬레이션 해볼 수 있는 애플리케이션입니다.

- [바로가기](#바로가기)
- [프로젝트 정보](#프로젝트-정보)
  - [언어](#언어)
  - [기술](#기술)
  - [아키텍처](#아키텍처)
- [노트](#노트)
- [스크린샷](#스크린샷)


## 바로가기

- [Github](https://github.com/namhyun-gu/BitcoinSimulator)

## 프로젝트 정보

### 언어

- Kotlin

### 기술

- **Android Architecture Component (AAC)**
- **RxJava**
- Retrofit
- Realm database

### 아키텍처

- MVVM

## 노트

이 프로젝트는 비트코인 투자에 대한 열풍이 불었을 때 가상 투자를 통해 수익을 확인해보고자 개발한 프로젝트입니다.

이전과는 달리 처음으로 아키텍처 패턴으로 MVVM을 도입하면서 Android Architecture Component를 활용한 프로젝트입니다.

프로젝트 내에서 RxJava는 빗썸 API을 이용할 때 주로 사용되었으며, 다음과 같이 Flowable를 사용하여 개발되었습니다.

- [TransactionViewModel.kt](https://github.com/namhyun-gu/BitcoinSimulator/blob/master/app/src/main/java/dev/namhyun/bitcoinsimulator/transaction/TransactionViewModel.kt)

```kotlin
class TransactionViewModel : ViewModel() {

    private val db: Realm = Realm.getDefaultInstance()

    private val bithumbService: BithumbService = BithumbServiceGenerator.generate()

    fun updatePrice(currencyName: String): Flowable<Ticker<Currency>>
            = Flowable.interval(500, TimeUnit.MILLISECONDS)
            .flatMap { bithumbService.getCurrencyTicker(currencyName) }
            .subscribeOn(Schedulers.io())
            .observeOn(AndroidSchedulers.mainThread())

    fun buyCurrency(currencyName: String, count: Float): Flowable<TransactionStatus> {
        return bithumbService.getCurrencyTicker(currencyName)
                .map { it.data.currentPrice }
                .subscribeOn(Schedulers.io())
                .observeOn(Schedulers.computation())
                .map { writeBuyTransaction(currencyName, count, it) }
                .observeOn(AndroidSchedulers.mainThread())
    }

    fun sellCurrency(currencyName: String, count: Float): Flowable<TransactionStatus> {
        return bithumbService.getCurrencyTicker(currencyName)
                .map { it.data.currentPrice }
                .subscribeOn(Schedulers.io())
                .observeOn(Schedulers.computation())
                .map { writeSellTransaction(currencyName, count, it) }
                .observeOn(AndroidSchedulers.mainThread())
    }

    // ...

}
```

## 스크린샷

<img src="https://raw.githubusercontent.com/namhyun-gu/BitcoinSimulator/master/screenshots/device-2017-12-27-102600.png" width="320">
<img src="https://raw.githubusercontent.com/namhyun-gu/BitcoinSimulator/master/screenshots/device-2017-12-28-111103.png" width="320">
<img src="https://raw.githubusercontent.com/namhyun-gu/BitcoinSimulator/master/screenshots/device-2017-12-27-102655.png" width="320">
