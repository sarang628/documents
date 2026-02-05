# [Macrobenchmark 작성하기](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview)
- app startup 이나 복잡한 UI와 같은 larger use cases에 사용
- 작은 use case는 Microbenchmark library 사용 권장
- Android Studio console 과 JSON file로 결과 제공 가능
- Android Studio에서 분석 가능한 trace files로도 제공
- CI(continuous integration) 환경에 추가 가능
- Baseline Profiles 생성을 위해 Macrobenchmark 사용
- Macrobenchmark setup 후 Baseline Profile 생성하기

## [Project setup](https://developer.android.com/topic/performance/benchmarking/macrobenchmark-overview#project-setup)
- 