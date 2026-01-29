App data

scoped

side effect

[composable](https://developer.android.com/reference/kotlin/androidx/compose/runtime/Composable)
- compose로 앱을 build 하는데 기본적인 building block
- 애플리케이션 데이터를 tree 또는 hierarchy 형태로 변환하는 composition을 describe하는데 사용.
  - 앱 데이터를 -> tree or hierarchy 형태로 변환
    - 컴포즈로 UI 구현 시 앱의 데이터를 tree or hierarchy 형태로 작성하게 된다.  
  - 위의 형태를 구성하는데 composable 들이 사용됨.
  - 선언형 패러다임을 사용하기때문에 이를 정의하고 표현하는 것을 describe로 사용
- composable은 어노테이션을 붙인다.
  - composable 함수는 composable만이 호출 할 수 있음.
  - 이 방식이 compose 내부적으로 트리 형태에서 각 composable의 정보를 유지할 수 있음.
- [Basics of composable functions](https://developer.android.com/develop/ui/compose/layouts/basics#composable-functions)
  - UI의 일부인 Unit을 방출(emit)하는 함수이다.
  - 데이터를 받으면 UI를 화면에 표시해줌.
- [Composable 함수 예](./compose/2_ThinkingInCompose.md)


[DSL](https://en.wikipedia.org/wiki/Domain-specific_language)
- 특정 애플리케이션 도메인에 특화된 언어
- general-purpose language (GPL) 과 대조되는 개념
- HTML과 같이 일부 소프트웨어에서 사용되는 언어