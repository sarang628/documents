# [Lifecycle of composables](https://developer.android.com/develop/ui/compose/lifecycle?_gl=1*415ei0*_up*MQ..*_ga*MTM1NjY4NzYwMS4xNzY5NDc2OTY3*_ga_6HH9YJMN9M*czE3Njk0NzY5NjckbzEkZzAkdDE3Njk0NzY5NjckajYwJGwwJGgxMjYwMDAxOTQ1)
- composable 함수에는 lifecycle가 존재함.
- Compose가 어떻게 composable의 recomposition을 결정하는지 배우기

## [lifecycle 개요](https://developer.android.com/develop/ui/compose/lifecycle?_gl=1*mjizbz*_up*MQ..*_ga*NjU5MjUwOTE4LjE3Njk0OTUxMDM.*_ga_6HH9YJMN9M*czE3Njk0OTUxMDIkbzEkZzAkdDE3Njk0OTUxMDIkajYwJGwwJGgxNzgxMTM1Njgy#lifecycle-overview)
- composition은 앱의 UI를 describe 한다.
  - composition은 실행되는(running) composable들로 부터 만들어짐
  - composition은 composable들로부터 만들어진 tree구조로 UI를 describe
- 최초 구성(initial composition)
  - Jetpack Compose는 처음에 composable를 실행하는 단계
  - 이때 composable들을 추적
- 재구성(recomposition)
  - 그리고 앱의 상태가 변하면 Jetpack Compose는 재구성(recomposition)을 스케줄
  - recomposition은 Jetpack Compose가 앱의 상태 변화에 따라 필요한 composable들을 재실행
  - 그리고 Jetpack Compose은 어떤 변화에 대해 컴포지션(Composition)을 업데이트
- 컴포지션(Composition)
  - 최초 구성(initial composition) 과 재구성(recomposition)에 의해서만 컴포지션(Composition)이 생성됨. (대문자 composition 구분하기)
  - 컴포지션(Composition)을 수정하는 방법은 오직 재구성(recomposition)으로만 가능
- composable 생명주기(lifecycle) 
  - enter Composition
  - recompose 0 or more times
  - leaving the Composition.
- 주로 State<T> 객체에 의해 재구성(recomposition)이 발생
  - State<T> 변경 시 이 객체를 참조하는 모든 composable 재구성 발생
- composable을 여러번 호출 시 각 호출별 instance가 새로 생성되고 각자 lifecycle을 갖음

## [컴포지션에서 composable의 해부](https://developer.android.com/develop/ui/compose/lifecycle?_gl=1*mjizbz*_up*MQ..*_ga*NjU5MjUwOTE4LjE3Njk0OTUxMDM.*_ga_6HH9YJMN9M*czE3Njk0OTUxMDIkbzEkZzAkdDE3Njk0OTUxMDIkajYwJGwwJGgxNzgxMTM1Njgy&utm_source=android-studio-app&utm_medium=app#composition-anatomy)
- 컴포지션 안의 composable 인스턴스의 식별은 **call site**로 함.
  - call site : composable가 호출되는 소스코드 상의 위치
  - recomposition 이 발생하더라도 모든 호출이 별개의 call site를 갖음.
- 컴포즈 컴파일러가 call site를 별개로 간주
- 어떤 조건문에 의해 recomposition 시 서로다른 composable를 호출한 경우
  - 그 이후에 컴포즈는 조건문에 의해 다르게 호출된 composable에서 어떤 것이 현재 호출된 상태인지 알 수 있다.
  - 컴포즈는 입력값이 변하지 않은 composable에 대해 재구성을 피한다.

## [스마트한 재구성을 위한 추가 정보](https://developer.android.com/develop/ui/compose/lifecycle?_gl=1*mjizbz*_up*MQ..*_ga*NjU5MjUwOTE4LjE3Njk0OTUxMDM.*_ga_6HH9YJMN9M*czE3Njk0OTUxMDIkbzEkZzAkdDE3Njk0OTUxMDIkajYwJGwwJGgxNzgxMTM1Njgy&utm_source=android-studio-app&utm_medium=app#add-info-smart-recomposition)
- 여러번 composable를 호출하는 것은 Composition에도 여러번 추가하는 것이 됨
- for 문과 같이 하나의 call site에서 여러번 호출한다면?
- Compose는 다른 식별자를 갖지 못함.
- 이런 개채 식별을 위해 call site에 **순서(order)**를 추가 정보로 갖음
- 때로는 이 정보로 모든게 해결되기도 하지만 그렇지 않은 경우도 있음
  - 리스트에서 마지막에 항목이 추가되는 것은 문제가 되지 않음.(화면은 그대로 멈춰있기 때문)
  - 최상단이나 가운데 추가된다면?
    - 리스트가 재정렬되면서 기존 인덱스와 다른 정보를 가진 모든 항목이 재구성(recomposition) 됨
    - 이미지를 로드중에 위 이벤트 발생 시 기존 이미지 로드를 취소하고 새로운 정보로 다시 이미지 로드 시작
- 리스트 중간이 데이터 추가 시 기존 인스턴스를 유지하며 그 사이에 새로운 인스턴스를 추가하는것을 이상적으로 생각
  - key를 사용하면 위위 방법을 사용할 수 있게 함

## [입력값이 변하지 않았다면 skip](https://developer.android.com/develop/ui/compose/lifecycle?_gl=1*mjizbz*_up*MQ..*_ga*NjU5MjUwOTE4LjE3Njk0OTUxMDM.*_ga_6HH9YJMN9M*czE3Njk0OTUxMDIkbzEkZzAkdDE3Njk0OTUxMDIkajYwJGwwJGgxNzgxMTM1Njgy&utm_source=android-studio-app&utm_medium=app#skipping)
- skip 불가능한 경우
  - return이 Unit(void)가 아닌 경우
  - @NonRestartableComposable or @NonSkippableComposable를 붙인 경우
  - non-stable type의 파라미터인 경우
    -  Strong Skipping 모드로 위의 경우를 완화 할 수 있음
- stable type을 만드는 방법
  - 같은 인스턴스는 항상 equals값이 동일해야함
  - public property 변경 시 컴포지션에게 알려져야함
  - 모든 public property 타입들도 stable 해야함
- @stable 안써도 stable 인 값
  - 프리미티브 타입 : Boolean, Int, Long, Float, Char
  - Strings
  - All function types (lambdas)
  - 변경할 수 없는 immutable 데이터 이기 때문
- MutableState은 변경가능(mutable) 하지만 특별한 stable 타입
- 