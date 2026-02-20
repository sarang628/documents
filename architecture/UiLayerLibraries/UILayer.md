# [UI layer](https://developer.android.com/topic/architecture/ui-layer)
- UI
  - application data를 display
  - user interaction의 primary point
  - 데이터 변경 발생 시 이를 반영한 UI 업데이트
  - UI는 data layer에서 가져온 앱의 상태의 시각화를 나타내는 것
- Data Layer에서 받은 애플리케이션 데이터를 UI로 표시하는것이 효율적
- 하지만 Data Layer에서 가져온 데이터 포맷을 바로 UI에 표시하기는 적절하지 않음
- UI는 하나 이상의 data source의 데이터가 합쳐져야 하는 경우도 있음
- UI Layer가 이 UI가 필요한 데이터의 파이프라인 역할을 함

# [A basic case study](https://developer.android.com/topic/architecture/ui-layer#case-study)
- udf 이론을 도입하는 예제를 보여줌
- 문제들을 이론들이 어떻게 도움을 주는지 확인

# [UI layer architecture](https://developer.android.com/topic/architecture/ui-layer#architecture)
- UI는 activity, fragment와 같이 ,(View나 Compose와 같은) 어떤 API를 사용하는 것과는 독립적으로, 데이터를 표시하는 요소를 의미
- data layer는 app data를 접근, 수정, 관리, 제공 등을 책임
- UI layer의 역할
  - 앱 데이터를 소비하여 UI를 그리기 사용하기 쉬운 데이터로 변환
  - UI-renderable 데이터를 UI elements가 표시를 하도록 변환
  - 사용자의 입력을 받아 그 effects를 필요로 하는 UI data에 반영
  - 위 3가지를 반복
- 이 장의 가이드가 다루는 작업들와 개념(tasks and concept)
  - UI state 정의 방법
  - UI state를 생성하고 관리하는 수단으로서의 UDF
  - UDF 개념에 따라 observable 하게 UI state를 노출하는 방법
  - observable UI state 소비하여 UI를 구현하는 방법

## [Define UI state](https://developer.android.com/topic/architecture/ui-layer#define-ui-state)
- 