# [Lists and grids](https://developer.android.com/develop/ui/compose/lists)
- Column은 보이지 않는 항목까지 모두 로드하기 때문에, 많은 항목들을 만들 때 성능상 좋지 않음
- LazyColumn은 항목이 많아도 보이는 항목만 로드
- LazyListScope를 제공하여, @Composable 컨튼츠 블록 파라미터를 받지않고 대신 composable가 emit하는 것을 바로 받음
- LazyListScope는 리스트 항목을 작성하는 DLS를 제공
- Lazy component는 레이아웃과 스크롤 위치에 따라 항목을 추가하는 역할을 함

## [LazyListScope DSL](https://developer.android.com/develop/ui/compose/lists#lazylistscope)
- LazyListScope의 DSL은 항목을 만드는 여러 함수를 제공
- item() 항목을 추가하는 함수 
- items() 에는 항목의 개수, 리스트 type을 넣을 수 있다.

## [Content padding](https://developer.android.com/develop/ui/compose/lists?utm_source=android-studio-app&utm_medium=app#content-padding)
- layout가 아닌 content에 패딩을 설정
- vertical을 설정하면 첫번째 항목과 마지막 항목에 각각 위 아래로 패딩이 생김
- horizontal을 설정하면 모든 항목에 좌우로 패딩이 생김

## [Item keys](https://developer.android.com/develop/ui/compose/lists?utm_source=android-studio-app&utm_medium=app#item-keys)
- 기본적으로 위치가 key로 설정
- 하지만 리스트의 항목의 순서가 바뀌는 등의 데이터 변경이 일어나면 List UI는 상태를 잃어버림.
- 이 경우 사용자는 리스트 스크롤 위치를 잃어버림
- 키의 타입은 Bundle에서 지원하는 값이여야 함 (primitives, enums, Parcelable, etc.)
- bundle에서 지원 하는 타입만이 rememberSaveable에서 사용가능 하고 composable 재생성 시 이 값을 복구 할 수 있음

