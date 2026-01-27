## [선언형 프로그래밍 패러다임](https://developer.android.com/develop/ui/compose/mental-model#paradigm)
- 전통적으로 뷰 계층(hierarchy)은 tree 형태로 표현
    - 앱의 상태가 바뀌면 해당 뷰의 요소를 찾아 변경
    - 화면이 복잡해 질수록 오류 발생이 높아짐
- 전반적인 산업에서 선언형 모델로 전환
- 전체 화면을 다시 그리되 변경이 필요한 것만 적용.
- 화면을 다시 그리는 것은 비용이 높음
- 컴포즈는 필요한 부분만 다시 그리는 최적화된 방법인 recomposition을 적용

## [Composable 함수 예](https://developer.android.com/develop/ui/compose/mental-model?utm_source=android-studio-app&utm_medium=app#simple-example)

- 어노테이션(Annotation)
    - 컴포즈 컴파일러에 이 함수는 UI가 될 것임을 알림
- 데이터 입력(Data input)
    - 앱의 로직을 UI로 보여주는 파라미터
- UI를 표시(UI display)
    - UI를 표시해주는 컴포즈 라이브러리를 호출
- 리턴 값 없음(No return value)
    - 리턴 값 없이 화면에 UI를 방출
- 속성들(Properties)
    - 빠르고, 멱등성, 사이드 이펙트 free
    - 전역변수나 random() 등을 사용하지 않아 (동시에)여러번 호출해도 결과가 동일 = 멱등성(idempotent)
    - 속성이나 전역변수 변경들을 하지 않고 UI만 그림

## [선언형 프로그래밍 패러다임 전환 (The declarative paradigm shift)](https://developer.android.com/develop/ui/compose/mental-model?utm_source=android-studio-app&utm_medium=app#declarative-paradigm-shift)
- 기존 안드로이드 명령형(imperative) UI는 getter setter로 설정할 수 있게 각 위젯이 상태를 가지고 있음.
- 컴포즈의 선언형(declarative) 접근은 상대적으로 상태를 갖지 않도록 함.
- 위젯이 객체로서 노출되지 않음.
- 같은 composable 함수를 호출함으로써 UI를 변경
- 이는 아키텍처적 패턴들에서 상태 제공을 단순화함
- 앱의 상태를 관찰 가능한 데이터로 만들어 composable가 상태 변화에 자동으로 UI를 업데이트 하도록 구성.
- 사용자 이벤트 발생 시, 앱의 상태를 오직 바꿀 수 있는 **앱의 로직**에 알림.
- 로직 수행 후 앱의 상태가 바뀌면 자동으로 컴포즈가 다시 그려짐 이 과정을 recomposition 이라고 함.

## [동적 컨텐츠(Dynamic content)](https://developer.android.com/develop/ui/compose/mental-model?utm_source=android-studio-app&utm_medium=app#dynamic)
- 단순 UI만 표시하는 xml 기반에서는 할 수 없었던
- 작은 요소 UI에 필요한 로직을 적용해 바로 확인할 수 있다.

## [재구성(Recomposition)](https://developer.android.com/develop/ui/compose/mental-model?utm_source=android-studio-app&utm_medium=app#recomposition)
- 명령형 UI모델에서는 위젯 변경을 위해 내부 상태에 접근해 변경
- 컴포즈는 함수를 다시 호출해 UI를 변경. 재구성(recompose)를 야기함
- 앱에서 보여지는 변화를 side-effects라고 한다.
- composable 함수는 side-effects에 의존하면 안된다.
- 위험한 side-effects 행동
  - 공통 오브젝트에 속성을 작성하는 것
  - 뷰모델의 관측 가능한(observable) 변수를 변경하는 것
  - shared preference를 변경하는 것
### [recomposition 시 가능한 많이 skip하기](https://developer.android.com/develop/ui/compose/mental-model?utm_source=android-studio-app&utm_medium=app#skips)
### [주의: recomposition의 낙관적 수행](https://developer.android.com/develop/ui/compose/mental-model?utm_source=android-studio-app&utm_medium=app#optimistic)
  - recomposition에 파라미터가 변경되는 경우?
  - recomposition이 취소되고 다시 새로운 파라미터로 recomposition 수행
  - UI가 그려지는 곳에 사이드 이펙트가 의존한다면 recomposition이 취소 되더라도 해당 사이트 이펙트는 실행될 수 있음.
    - ex) 컴포즈 안에 Log를 그냥 호출 (여러번 호출될 수 있음)
    - Composable 본문에서는 사이드 이펙트를 직접 실행하면 안 됨
### [composable 함수는 꽤 자주 실행될 수 있음](https://developer.android.com/develop/ui/compose/mental-model?utm_source=android-studio-app&utm_medium=app#frequent)
  - UI 애니메이션의 매 프레임마다 실행 될 수 있음
  - 기기 storage 읽기와 같은 비싼 수행은 Jank를 발생 가능
  - 다른 쓰레드에서 수행 observable 데이터 타입을 사용하여 업데이트
### [composable 함수는 병렬로 실행 할 수 있음](https://developer.android.com/develop/ui/compose/mental-model?utm_source=android-studio-app&utm_medium=app#parallel)
  - 기본적으로는 수직이지만 멀티 쓰레드 사용 시 병렬이 될 수 있음
  - 병렬 수행 시 낮은 우선순위의 화면에 없는 composable 함수가 실행될 수 있음
  - composable 함수는 side-effects가 없어야 한다(should).
  - 대신 UI thread에서 수행을 요청하는 onClick과 같은 triggered side effect 사용
  - composable 다른 thread에 의해 호출 될 수 있다. composable 람다와 같은 곳에서
  - 이런 composable 람다와 같은 곳에선 변수를 수정하지 않도록 한다. thread-safe 하지 않음.
### [composable은 순서에 관계 없이 실행될 수 있음](https://developer.android.com/develop/ui/compose/mental-model?utm_source=android-studio-app&utm_medium=app#any-order)
  - composable는 main thread에서 수행되지만, 안에서 수행은 multithreading로 하도록 설계
  - 내부적으로 UI elements에 그리는 우선순위가 있기때문에 composable 안에서 다른 여러 composable를 호출하면 순서대로 실행 안됨. 