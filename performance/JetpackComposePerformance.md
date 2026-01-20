# [Jetpack Compose Performance](https://developer.android.com/develop/ui/compose/performance?_gl=1*1o97pst*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5)

## [성능을 위한 3가지 핵심 컨셉](https://developer.android.com/develop/ui/compose/performance?_gl=1*1o97pst*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#key_concepts)

- Phases : 
  - compose 최적화를 위해선 composition, layout, drawing phases를 이해 필요.
  - 어떻게 UI 업데이트를 최적화 하는지 이해
- Baseline Profiles
  - 주요 코드를 미리 컴파일
  - 빠른 앱 실행과 부드러운 상호작용을 이끈다.
- Stability
  - 효과적으로 불필요한 recomposition을 skip 

## [적절하게 앱 설정하기](https://developer.android.com/develop/ui/compose/performance?_gl=1*1o97pst*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#config)
- 릴리즈 모드와 R8 컴파일러 사용
- Baseline Profiles 사용

## [Tools](https://developer.android.com/develop/ui/compose/performance?_gl=1*1o97pst*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#tools)
- Layout Inspector나 Composition tracing 같은 도구 사용하기

## [Best Practices]
- [비싼 계산 피하기](https://developer.android.com/develop/ui/compose/performance/bestpractices?_gl=1*17qwznr*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#use-remember) : 비싼 계산 결과 저장을 위해 remember 사용
- [lazy layout](https://developer.android.com/develop/ui/compose/performance/bestpractices?_gl=1*bsnk04*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#use-lazylist-keys) : 항목에 key값을 설정하여 불필요한 recomposition 최소화 가능
- [불필요한 recomposition 제한](https://developer.android.com/develop/ui/compose/performance/bestpractices?_gl=1*18ajmtf*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#use-derivedstateof) : 빠르게 변하는 상태는 derivedStateOf를 사용해 recomposition 제한 가능
- [지연 상태 읽기](https://developer.android.com/develop/ui/compose/performance/bestpractices?_gl=1*18ajmtf*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#defer-reads) : 람다 함수로 감싸 가능한 상태 읽기를 지연 시키기
- [상태 변화에 람다 modifier 사용하기](https://developer.android.com/develop/ui/compose/performance/bestpractices?_gl=1*cdg47c*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#defer-reads) : 자주 변하는 상태에 대해 람다 기반 modifier 사용하기
- [역방향 쓰기 피하기](https://developer.android.com/develop/ui/compose/performance/bestpractices?_gl=1*16ni68f*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#avoid-backwards) : 이미 읽은 상태 변경하기 않기

## [Views](https://developer.android.com/develop/ui/compose/performance?_gl=1*1s94nda*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#views)
- 뷰와 함께 사용하는경우.

## [추가 자료](https://developer.android.com/develop/ui/compose/performance?_gl=1*1s94nda*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5#additional_resources)
- [App performance guide](https://developer.android.com/topic/performance/overview?_gl=1*19kg4yy*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5)
- [Inspect Performance](https://developer.android.com/topic/performance/inspecting-overview?_gl=1*5aiuuh*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5)
- [Benchmarking](https://developer.android.com/topic/performance/benchmarking/benchmarking-overview?_gl=1*5aiuuh*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5)
- [App startup](https://developer.android.com/topic/performance/appstartup/analysis-optimization?_gl=1*5aiuuh*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5)
- [Baseline profiles](https://developer.android.com/baseline-profiles?_gl=1*5aiuuh*_up*MQ..*_ga*MTc4NTM1NDg0OC4xNzY4ODcwNDE0*_ga_6HH9YJMN9M*czE3Njg4NzA0MTMkbzEkZzAkdDE3Njg4NzA0MTMkajYwJGwwJGgxNzMyODQ2NzA5)