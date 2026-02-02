# [Benchmark your app](https://developer.android.com/topic/performance/benchmarking/benchmarking-overview)
- Benchmark는 앱의 퍼포먼스를 조사 및 모니터
- Macrobenchmark, Microbenchmark 두가지 밴치마크 라이브러리를 제공

## [Macrobenchmark](https://developer.android.com/topic/performance/benchmarking/benchmarking-overview#macrobenchmark)
- 큰 사용자 상호작용을 측정
- 시작, UI 상호작용, 애니메이션
- 테스트 중인 성능 환경을 직접 제어할 수 있는 기능을 제공
- 개발자가 컴파일을 제어, 앱을 시작 및 중지 제어를 통해 앱의 시작 이나 스크롤의 성능을 직접 측정할 수 있게 함
- 테스트앱에 이벤트들을 주입, 결과를 모니터
- 벤치마크 작성시 앱의 코드를 직접 호출하지 않고 사용자로서 앱을 사용

## [Microbenchmark]
- 앱의 코드를 직접 밴치마크
- 