# [Macrobenchmark 작성하기](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview)
- app startup 이나 복잡한 UI와 같은 larger use cases에 사용
- 작은 use case는 Microbenchmark library 사용 권장
- Android Studio console 과 JSON file로 결과 제공 가능
- Android Studio에서 분석 가능한 trace files로도 제공
- CI(continuous integration) 환경에 추가 가능
- Baseline Profiles 생성을 위해 Macrobenchmark 사용
- Macrobenchmark setup 후 Baseline Profile 생성하기

## [Project setup](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview#project-setup)
- Macrobenchmark가 통합된 안드로이드 스튜디오 최신버전 사용을 권장

### [Setup the Macrobenchmark module](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview?utm_source=android-studio-app&utm_medium=app#setup-macrobenchmark)
- 테스트와 측정을 위한 com.android.test 모듈 필요. (앱 실제 구현 코드와 분리)
- 안드로이드 스튜디오에 쉽게 자동 설정 해주는 메뉴가 있음


### [Set up the app](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview?utm_source=android-studio-app&utm_medium=app#set-up-app)
- 성능에 영향을 주지 않고 정보를 추적하는 profileable 을 설정해야 함
- AndroidManifest.xml에 <profileable> 추가하여 설정
- ProfilerInstaller 1.3 이상 버전 설정 해야함
  - Macrobenchmark 라이브러리가 profile capture와 reset 과 shader cache clearing 해줌
- 가능한 릴리즈나 프로덕션 버전으로 설정하기

### [(Optional) Set up multi-module app](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview?utm_source=android-studio-app&utm_medium=app#multi-module)
- 하나 이상의 모듈로 구성되어 있다면, 빌드 스크립트들은 어떤 빌드 변수로 컴파일하는지 알아야 한다.

### [(Optional) Set up product flavors](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview?utm_source=android-studio-app&utm_medium=app#product-flavors)
- 여러개의 flavors가 있다면 벤치마크가 어떤 flavor을 사용할지 명시해줘야 함

#### [Use missingDimensionStrategy](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview?utm_source=android-studio-app&utm_medium=app#use_missingdimensionstrategy)
- 위에 말한 flavors가 여러게 있을때 명시해주는 방법
```
defaultConfig {
    missingDimensionStrategy("environment", "production")
}
```

#### [Define product flavors in the :macrobenchmark module](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview?utm_source=android-studio-app&utm_medium=app#define_product_flavors_in_the_macrobenchmark_module)
- productFlavors to a dimension 만 추가함으로써 벤치마크 모듈에 flavor을 추가 가능

### [Create a macrobenchmark class](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview?utm_source=android-studio-app&utm_medium=app#create-macrobenchmark)
- MacrobenchmarkRule : JUnit4 룰로 Macrobenchmark 라이브러리에서 제공해줌
- measureRepeated : 벤치마크 할 수 있는 다양한 옵션을 제공하는 함수
- 