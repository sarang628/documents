# [앱 아키텍처](https://developer.android.com/topic/architecture)
- 확장성과 유지보수 하기 좋은 앱을 만들 수 있음.
- 폰, 태블릿, 폴더블, XR등 다양한 안드로이드 기기에 확장 적용할 수 있음.

## [앱 구성](https://developer.android.com/topic/architecture#app_composition)
- 전통적으로 안드로이드 앱은 액티비티, 서비스, 브로드케스트 리시버, 컨텐트 프로바이더 등 앱 컴포넌트로 구성됨.
- UI도 앱의 컴포넌트로 여러 액티비티로 구성되어옴
- 하지만 근래에는 하나의 액티비티에 프레그먼트나 잿팻 컴포즈로 UI를 구현하도록 변화함.
- [Multiple form factors](https://developer.android.com/topic/architecture#form-factors)
  - 폰, 테블릿, 폴더블과 가로 세로 등 다양한 화면이 보편화되며 앱은 이들 화면에 대한 지원 필요
- [리소스 제약](https://developer.android.com/topic/architecture#resource-constraints)
  - 큰 기기라도 자원의 제약으로 운영제체는 앱을 언제라도 종료 시킬 수 있다.
- [다양한 실행 조건](https://developer.android.com/topic/architecture#launch-conditions)
  - 앱 컴포넌트는 언제든 종료될 수 있으므로 데이터를 저장하면 안됨. 컴포넌트는 독립적이여야 함.