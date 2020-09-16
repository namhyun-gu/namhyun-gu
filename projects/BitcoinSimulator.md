# BitcoinSimulator

> Bithumb의 비트코인 시세 API를 통해 비트코인 투자를 시뮬레이션 해볼 수 있는 애플리케이션입니다.

### 바로가기

- [Github](https://github.com/namhyun-gu/BitcoinSimulator)

### 사용한 언어

- Kotlin

### 사용한 기술

- **Android Architecture Component (AAC)**
- **RxJava**
- Retrofit
- Realm database

### 아키텍처

- MVVM

### 노트

이 프로젝트에서는 처음으로 아키텍처 패턴으로 MVVM을 도입하였습니다.
MVVM에 RxJava의 Flowable를 이용하여 개발되었으며 이는 주로 빗썸 API를 다룰때 주로 이용되었습니다.

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

### 스크린샷

<img src="https://raw.githubusercontent.com/namhyun-gu/BitcoinSimulator/master/screenshots/device-2017-12-27-102600.png" width="320">
<img src="https://raw.githubusercontent.com/namhyun-gu/BitcoinSimulator/master/screenshots/device-2017-12-28-111103.png" width="320">
<img src="https://raw.githubusercontent.com/namhyun-gu/BitcoinSimulator/master/screenshots/device-2017-12-27-102655.png" width="320">
