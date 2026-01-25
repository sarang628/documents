# [UI layer](https://developer.android.com/topic/architecture/ui-layer)
- UI
  - 애플리케이션 데이터를 화면에 표시
  - 사용자와 상호작용의 주 시작점
- Data Layer에서 받은 애플리케이션 데이터를 UI로 표시하는것이 효율적
- 하지만 Data Layer에서 가져온 데이터 포맷을 바로 UI에 표시하기는 적절하지 않음
- UI는 하나 이상의 data source의 데이터가 합쳐져야 하는 경우도 있음
- UI Layer가 이 UI가 필요한 데이터의 파이프라인 역할을 함

# [A basic case study](https://developer.android.com/topic/architecture/ui-layer#case-study)
- udf 이론을 도입하는 예제를 보여줌
- 문제들을 이론들이 어떻게 도움을 주는지 확인

# [UI layer architecture](https://developer.android.com/topic/architecture/ui-layer#architecture)
- UI는 activity, fragment와 같이 데이터를 표시하는 요소를 의미(View나 Compose와 같은 API와는 독립적임??)