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
- skippable, restartable로 마크 가능. 하나 또는 둘 또는 아무것도 마크하지 않을 수도 있음
- Skippable: 모든 파라미터가 이전과 같다면 컴포즈는 skip 가능한 skippable를 mark
- Restartable: 상태 변경 시 Compose가 코드를 재시작하는 지점으로 지정. restartable은 이를 scope로 제공한다고 표현

### [Types](https://developer.android.com/develop/ui/compose/performance/stability?utm_source=android-studio-app&utm_medium=app#types)
- immutable 또는 stable 타입으로 mark
- Immutable: 값이 바뀌지 않을 경우. (모든 primitive type은 Immutable)
- Stable: 생성 후에 바뀔 수 있는 값. 런타임에 변경 시 Compose는 이 변화를 알게된다.
- Composable parameters는 skip을 위해 immutable일 필요는 없다.
  - mutable 이라면 Compose runtime 모든 변화를 notify 받는다.
  - 대부분의 tpye에서 이런 contract를 지키는건 불가능
  - 그래서 Compose 이런 contract 지켜주는 MutableState, SnapshotStateMap, SnapshotStateList와 같은 mutable classes를 제공


## [Debug stability](https://developer.android.com/develop/ui/compose/performance/stability?utm_source=android-studio-app&utm_medium=app#debug-stability)
- 앱이 파라미터 변화가 없었던 composable를 recomposing 중이라면 parameters가 mutable인지 확인
- var 타입이거나 unstable type으로 알려진 val 타입의 경우 항상 recompose


## [Fix stability issues](https://developer.android.com/develop/ui/compose/performance/stability?utm_source=android-studio-app&utm_medium=app#fix-stability)


## [Summary](https://developer.android.com/develop/ui/compose/performance/stability?utm_source=android-studio-app&utm_medium=app#summary)
- Parameters: 어떤 composables이 skip 대상인지 결정을 위한 각 parameter에 stability를 결정
- Immediate fixes: skip이 안돼 성능 이슈 발생 시 var와 같은 타입 체크로 바로 확인 가능한 방법 사용
- [Compiler reports](https://developer.android.com/develop/ui/compose/performance/stability/diagnose?_gl=1*14ng1a9*_up*MQ..*_ga*Mjc0NTgxMDc1LjE3NzE0OTMzODc.*_ga_6HH9YJMN9M*czE3NzE0OTMzODckbzEkZzAkdDE3NzE0OTMzODckajYwJGwwJGgxMjMyNDcxMzM5): compiler reports 사용하여 클래스에 대해 stability가 추론되는지 확인 가능
- Collections: List, Set, Map과 같은 타입은 항상 unstable로 취급. immutable로 guaranteed를 할 수 없음. 
  - @Immutable or @Stable를 사용하거나 [Kotlinx immutable collections](https://developer.android.com/develop/ui/compose/performance/stability/fix?_gl=1*1fgijet*_up*MQ..*_ga*MTA5Njk5NzMzMC4xNzcxNDkzNDE0*_ga_6HH9YJMN9M*czE3NzE0OTM0MTMkbzEkZzAkdDE3NzE0OTM0MTMkajYwJGwwJGgxMzgxNTgxMzc2#immutable-collections)사용하기
- Other modules: Compose compiler이 동작하지 않는 모듈은 unstable로 간주. 필요시 UI model classes로 Wrap 하기