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

## [LaunchedEffect: composable에서 suspend 함수 사용](https://developer.android.com/develop/ui/compose/side-effects?utm_source=android-studio-app&utm_medium=app#launchedeffect)
- LaunchedEffect가 Composition으로 들어가면(enter) 파라미터로 코드블럭을 통과하는 coroutine를 실행한다.
- LaunchedEffect가 Composition을 떠나면(leaves) coroutine는 취소된다.
- LaunchedEffect가 다른 키값으로 재구성되면 기존 실행중인 coroutine이 취소되고 새로운 coroutine 으로 실행

## [rememberCoroutineScope: composable 밖에서 coroutine를 실행할 composition scope를 얻음](https://developer.android.com/develop/ui/compose/side-effects?utm_source=android-studio-app&utm_medium=app#remembercoroutinescope)
- LaunchedEffect는 composable 함수로 composable 안에서만 사용 가능
- composable 밖에서 coroutine 사용시 composition이 끝나면 coroutine이 자동 취소됨. rememberCoroutineScope 사용 필요
- 한개 이상의 코루틴의 lifecycle를 수동으로 제어가 필요할 때도 rememberCoroutineScope이 필요
- rememberCoroutineScope은 composable 함수로 호출한 composable의 composition에 CoroutineScope 범위를 갖는다.

## [rememberUpdatedState: 값이 변경되어도 재시작하지 않아야 하는 effect에 값을 참조](https://developer.android.com/develop/ui/compose/side-effects?utm_source=android-studio-app&utm_medium=app#rememberupdatedstate)
- LaunchedEffect는 key 값 변경시 재시작
- 파라미터 변경으로 발생하는 effect의 값은 바꾸면서 recomposition이 발생하지 않게 하는 방법
- 한번만 실행되야 하거나 오랫동안 동작하는 composable에서 recomposition없이 값만 변경할 때 유용

## [DisposableEffect: 정리가 필요한 effect](https://developer.android.com/develop/ui/compose/side-effects?utm_source=android-studio-app&utm_medium=app#disposableeffect)
- 키 변경이나, composition 을 leave할 때 정리하는 동작을 필요로 할 때

## [SideEffect: non compose 코드에 compose state를 배포](https://developer.android.com/develop/ui/compose/side-effects?utm_source=android-studio-app&utm_medium=app#sideeffect-publish)
- compose에서 관리되지 않는 compose상태를 객체와 함께 공유를 위해 사용
- 매 recomposition이 성공할 때 마다 실행을 보장
- composable에서 effect를 바로 작성하면 effect는 호출됬지만 composable은 도중에 취소 될 수 있어 비정상 적으로 동작할 수 있음

## [produceState:non-Compose state 를 Compose state 변경]
- 