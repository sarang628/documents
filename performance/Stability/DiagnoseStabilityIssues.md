# [Diagnose stability issues](https://developer.android.com/develop/ui/compose/performance/stability/diagnose)

- 불필요 하거나 과도한 recomposition으로 성능 이슈를 경험중이라면, 앱의 stability를 디버깅 해야함.
- 불필요 하거나 시기상조인 최적화 지양
- 성능 측정을 위해 Macrobenchmark 사용해보기

## [Layout Inspector](https://developer.android.com/develop/ui/compose/performance/stability/diagnose#layout-inspector)
- 안드로이드 스튜디오의 Layout Inspector은 recomposing을 보여준다
- recompose와 skip한 횟수를 보여줌

## [Compose compiler reports](https://developer.android.com/develop/ui/compose/performance/stability/diagnose#compose-compiler)
- compose compiler은 stability 추론의 결과를 출력할 수 있다.
- 이 결과로 어떤 composable이 skippable 한지 알 수 있다.
- 실제 성능 이슈 발생 시 사용 모든 composable를 skippable로 만드는 시기상조 최적화 시 유지보수 어려움을 겪을 수 있음

### [Setup](https://developer.android.com/develop/ui/compose/performance/stability/diagnose#setup)

### [Example output](https://developer.android.com/develop/ui/compose/performance/stability/diagnose#example_output)
- <modulename>-classes.txt : 클래스의 stability 리포트
- <modulename>-composables.txt : restartable skippable Composable 리포트