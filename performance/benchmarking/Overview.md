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
- 앱의 코드를 loop안에서 직접 밴치마크
  - CPU 작업을 측정하도록 설계
  - best-case 성능 평가 (warmed up JIT나 캐시에 접근하는 디스크 등)
  - inner loop나 specific hot function을 볼 수 있다.
  - 직접 호출하거나 isolation되어있는 코드만 측정 가능
- 복잡한 데이터 구조나 앱 실행동안 여러번 호출되는 무거운 알고리즘 밴치마크 쓰기 좋은 사례
  - UI도 측정 가능
  - recyclerview의 item에 layout가 inflate 되는 시간 측정
  -  뷰의 measure와 layout을 통과하는데 얼마나 요구하는지 성능 관점에서 측정
- 벤치마크는 앱에서 어디가 성능상 문제가 있는지 알려주지 않음
  - Android profiler을 사용해서 의심되는 곳을 찾음
  - 벤치마크 루프에 해당 의심되는 코드를 호출한다
- 벤치마크 테스트는 시스템 전체와 관계없이 내 앱의 성능측정에만 초점을 둠
- 