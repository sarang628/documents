# [컴포즈 Side-effect](https://developer.android.com/develop/ui/compose/side-effects)
- Side-effect란 Composable 밖에서 상태가 변경되는 것
- 예상치 못한 recomposition 으로 recomposition들이 다른 순서로 발생 하거나 취소됨
- side-effect는 없는게 이상적
- 하지만 특정 조건에서 일회성 사이드 이펙트 필요
- composable 라이프사이클을 인지한 제한된 환경에서 이벤트를 다룰 수 있음

# [State와 effect 사용 사례](https://developer.android.com/develop/ui/compose/side-effects?utm_source=android-studio-app&utm_medium=app#state-effect-use-cases)
- 앱의 상태 변경 필요시 Effect API를 사용해야 적절한 시점에 side effect가 발생
- effect composable 함수이지만 UI를 방출하지 않고, composition 이 끝났을 때 side effect를 발생 시킴
- 다양한 이벤트 발생 가능성으로 과용될 수 있음
- unidirectional data flow를 해치지 않고 UI와 관련된 작업에만 사용
- 반응형 UI는 본질적으로 비동기
- Jetpack compose는 callback 사용 대신 coroutines을 사용하여 해결

## [LaunchedEffect : composable에서 suspend 함수 사용](https://developer.android.com/develop/ui/compose/side-effects?utm_source=android-studio-app&utm_medium=app#launchedeffect)
- LaunchedEffect가 Composition으로 들어가면(enter) 파라미터로 코드블럭을 통과하는 coroutine를 실행한다.
- LaunchedEffect가 Composition을 떠나면(leaves) coroutine는 취소된다.
- LaunchedEffect가 다른 키값으로 재구성되면 기존 실행중인 coroutine이 취소되고 새로운 coroutine 으로 실행

## [rememberCoroutineScope : composable 밖에서 coroutine를 실행할 composition scope를 얻음]
- LaunchedEffect는 composable 함수로 composable 안에서만 사용 가능
- composable 밖에서 coroutine 사용시 composition이 끝나면 coroutine이 자동 취소됨
- 