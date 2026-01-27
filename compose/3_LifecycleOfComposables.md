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