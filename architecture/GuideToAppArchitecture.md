# [앱 아키텍처](https://developer.android.com/topic/architecture)
- 확장성과 유지보수 하기 좋은 앱을 만들 수 있음.
- 폰, 태블릿, 폴더블, XR등 다양한 안드로이드 기기에 확장 적용할 수 있음.

## [앱 구성](https://developer.android.com/topic/architecture#app_composition)
- 전통적으로 안드로이드 앱은 액티비티, 서비스, 브로드케스트 리시버, 컨텐트 프로바이더 등 앱 컴포넌트로 구성됨.
- UI도 앱의 컴포넌트로 여러 액티비티로 구성되어옴
- 하지만 근래에는 하나의 액티비티에 프레그먼트나 잿팩 컴포즈로 UI를 구현하도록 변화함.
- [Multiple form factors](https://developer.android.com/topic/architecture#form-factors)
  - 폰, 테블릿, 폴더블과 가로 세로 등 다양한 화면이 보편화되며 앱은 이들 화면에 대한 지원 필요
- [리소스 제약](https://developer.android.com/topic/architecture#resource-constraints)
  - 큰 기기라도 자원의 제약으로 운영제체는 앱을 언제라도 종료 시킬 수 있다.
- [다양한 실행 조건](https://developer.android.com/topic/architecture#launch-conditions)
  - 앱 컴포넌트는 언제든 종료될 수 있으므로 데이터를 저장하면 안됨. 컴포넌트는 독립적이여야 함.

## [공통 아키텍처 원칙](https://developer.android.com/topic/architecture?utm_source=android-studio-app&utm_medium=app#common-principles)
- 앱의 규모가 커치면 앱의 확장, 앱의 각 부분의 경계와 경계간 역할의 명확한 구분이 필요.
- [관심사의 분리](https://developer.android.com/topic/architecture?utm_source=android-studio-app&utm_medium=app#separation-of-concerns)
  - 액티비티와 프레그먼트에 모든 코드를 구현하지 않기
  - 특히 컴포넌트에 앱의 데이터를 저장하지 않기
- [적응형 레이아웃](https://developer.android.com/topic/architecture?utm_source=android-studio-app&utm_medium=app#adaptive)
  - 앱은 환경 설정 변경에 유연하게 대처해야함.
  - 적응형 표준 레이아웃(Canonical layouts) 익혀 적용하기
- [데이터 모델로 UI를 제어](https://developer.android.com/topic/architecture?utm_source=android-studio-app&utm_medium=app#drive-ui-from-model)
  - 데이터 모델은 앱의 데이터를 나타낸다 이 모델은 지속 모델(persistent models) 권장.
  - UI와는 독립적인 데이터 모델이다.
  - 지속 모델(persistent models)은
    - OS에서 앱을 종료해도 사용자는 데이터를 잃지 않는다.
    - 네트워크가 간헐적으로 사용 불가해도 지속적으로 서비스를 유지한다.
  - 앱 아키텍처는 이 데이터 모델을 강력하고 테스트 가능하게 해준다.
- [Single source of truth](https://developer.android.com/topic/architecture?utm_source=android-studio-app&utm_medium=app#single-source-of-truth)
  - 특정 타입의 데이터 변경을 한곳으로 집중 할 수 있다.
  - 다른 타입에서는 데이터 변경이 불가. 데이터 보호
  - 데이터 변경을 추적하기 편해 디버깅에 용이

## [권장 앱 아키텍처](https://developer.android.com/topic/architecture?utm_source=android-studio-app&utm_medium=app#recommended-app-arch)
- UILayer, DataLayer 최소 2개의 레이어로 구성 (DomainLayer은 옵션으로 추가 가능)
- [모던 앱 아키텍처](https://developer.android.com/topic/architecture?utm_source=android-studio-app&utm_medium=app#modern-app-architecture)
  - (적응형)레이어화된 아키텍처
  - UDF
  - State holder가 있는 UILayer가 복잡한 UI를 제어
  - 코루틴과 플로우를 사용
  - 의존성 주입 권장
- [UILayer](https://developer.android.com/topic/architecture?utm_source=android-studio-app&utm_medium=app#ui-layer)
  - UI레이어의 역할은 화면에 앱의 데이터를 보여주는 것.
  - UI레이어는 UI element(such as Jetpack compose)와 state holder로 구성
- [DataLayer](https://developer.android.com/topic/architecture?utm_source=android-studio-app&utm_medium=app#data-layer)
  - 데이터 레이어는 비지니스 로직을 담고 있다.
  - 비지니스 로직은 앱에 어떤 값을 주는 것.
  - 비지니스 로직은 앱의 데이터를 생성, 저장, 수정하는 **비지니스 룰**들로 구성