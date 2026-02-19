# [Stability in Compose](https://developer.android.com/develop/ui/compose/performance/stability)

- Compose는 type들이 stable 한지 unstable 한지 고려
- stable : type이 immutable 하거나 recomposition 사이에서 값의 변경을 알 수 있는 경우
- unstable : recomposition 사이에 값이 변화를 알 수 없는 경우
- compose는 composable의 파라미터의 stability를 recomposition 시 skip 여부를 판단하는데 사용
- Stable parameters: 컴포즈가 skip하는 변치 않는 파라미터
- Unstable parameters : 부모가 recompose를 하면 항상 recompose를 파라미터
- 불필요한 Unstable parameters는 계속 recompose 되므로 성능에 영향을 줄 수 있음
- 사용자 경험과 성능 향상을 위해 **stability 향상** 필요

## [Immutable objects](https://developer.android.com/develop/ui/compose/performance/stability#immutable-objects)
- data 클래스의 parameters가 모두 val로 되어있는 경우
- 값 변경시 object를 새로 생성해야 함

## [Mutable objects](https://developer.android.com/develop/ui/compose/performance/stability#mutable-objects)
- data 클래스에 var가 포함된 경우

## [Implementation in Compose](https://developer.android.com/develop/ui/compose/performance/stability#implementation-compose)
- 컴파일러가 코드 실행 시 각 함수와 타입에 여러 태그들 중 하나를 붙임
- recomposition 시 skip여부를 판단하는데 사용

### [Functions](https://developer.android.com/develop/ui/compose/performance/stability?utm_source=android-studio-app&utm_medium=app#functions)