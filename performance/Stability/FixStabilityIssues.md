# [Fix stability issues](https://developer.android.com/develop/ui/compose/performance/stability/fix?_gl=1*u4suwv*_up*MQ..*_ga*MTc1NzE5MTcwNS4xNzcxNTQ3OTAx*_ga_6HH9YJMN9M*czE3NzE1NDc5MDEkbzEkZzAkdDE3NzE1NDc5MDEkajYwJGwwJGgzOTA3ODQ3MA..)
- unstable class stable로 고치는 방법

## [Enable strong skipping](https://developer.android.com/develop/ui/compose/performance/stability/fix?_gl=1*u4suwv*_up*MQ..*_ga*MTc1NzE5MTcwNS4xNzcxNTQ3OTAx*_ga_6HH9YJMN9M*czE3NzE1NDc5MDEkbzEkZzAkdDE3NzE1NDc5MDEkajYwJGwwJGgzOTA3ODQ3MA..#enable_strong_skipping)
- [strong skip 모드 활성화](https://developer.android.com/develop/ui/compose/performance/stability/strongskipping?_gl=1*kyqorf*_up*MQ..*_ga*MTc1NzE5MTcwNS4xNzcxNTQ3OTAx*_ga_6HH9YJMN9M*czE3NzE1NDc5MDEkbzEkZzAkdDE3NzE1NDc5MDEkajYwJGwwJGgzOTA3ODQ3MA..)

## [Make the class immutable](https://developer.android.com/develop/ui/compose/performance/stability/fix?_gl=1*u4suwv*_up*MQ..*_ga*MTc1NzE5MTcwNS4xNzcxNTQ3OTAx*_ga_6HH9YJMN9M*czE3NzE1NDc5MDEkbzEkZzAkdDE3NzE1NDc5MDEkajYwJGwwJGgzOTA3ODQ3MA..#make-class)
- Immutable: 생성 후 변하지 않는 값
  - var을 val로 바꾸기
  - Primitive 사용 (String, Int, and Float)
  - 위 변경이 불가한 경우, Compose state 사용하기
- Stable: 