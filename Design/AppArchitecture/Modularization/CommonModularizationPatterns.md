# [Common modularization patterns](https://developer.android.com/topic/modularization/patterns?_gl=1*1dlyu5c*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDA2NDAkbzEkZzAkdDE3NzIwMDA2NTgkajQyJGwwJGg3MTQ1MDQ4NjU.)
- 하나의 모듈화(single modularization) 전략이 맞는 앱은 없음.
- Gradle의 유연성으로 프로젝트를 어떻게 구성할지 거이 제약이 없다.

## [High cohesion and low coupling principle](https://developer.android.com/topic/modularization/patterns?_gl=1*1dlyu5c*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDA2NDAkbzEkZzAkdDE3NzIwMDA2NTgkajQyJGwwJGg3MTQ1MDQ4NjU.#cohesion-coupling)
- 모듈화된 코드베이스를 만드는 한 가지 방법은 coupling 과 cohesion 속성을 사용하는 것이다.
- Coupling은 하나의 모듈이 다른 모듈에 의존하는 것을 측정하는 것 이다.
- Cohesion은 하나의 모듈의 요소들이 기능적으로 연관되어있는지 측정하는 것
- Low coupling은 모듈들이 서로 연관이 적어 하나의 모듈이 변경되더라도 다른 모듈에 영향을 거이 주지 않는 것 
  - 모듈들은 다른모듈이 내부적으로 동작하는 지식을 갖고있지 않아야 한다.
- High cohesion은 모듈들이 코드들의 모음으로 이뤄져 시스템처럼 동작하는 것이다.
  - 특정 도메인 지식 안에서 명확한 책임을 갖는다
  - 예: ebook앱 -> book 모듈과 payment 모듈로 나눔

## [Types of modules](https://developer.android.com/topic/modularization/patterns?_gl=1*1dlyu5c*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDA2NDAkbzEkZzAkdDE3NzIwMDA2NTgkajQyJGwwJGg3MTQ1MDQ4NjU.#types-of-modules)
- 모듈을 organize하는 방법은 앱 아키텍처에 달려있다. [권장 아키텍처](https://developer.android.com/topic/architecture?_gl=1*1qzs2i0*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDcxMjAkbzIkZzAkdDE3NzIwMDcxMjAkajYwJGwwJGgxMjQyODcwOTY.) 참고

### [Data modules](https://developer.android.com/topic/modularization/patterns?_gl=1*1dlyu5c*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDA2NDAkbzEkZzAkdDE3NzIwMDA2NTgkajQyJGwwJGg3MTQ1MDQ4NjU.#data-modules)
- 데이터 모듈은 data source와 model classes가 있는 repository를 포함
- 이 모듈에는 3가지 주요 책임이 있음
  - 특정 도메인의 모든 데이터와 비지니스로직을 캡슐화
    - 각 데이터 모듈은 특정 도메인을 대표하는 데이터를 다루는 책임을 갖는다
  - 외부 API로 Repository를 제공
  - 세부 구현과 data source를 외부로부터 숨긴다

### [Feature modules](https://developer.android.com/topic/modularization/patterns?_gl=1*1dlyu5c*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDA2NDAkbzEkZzAkdDE3NzIwMDA2NTgkajQyJGwwJGg3MTQ1MDQ4NjU.#feature-modules)
- 앱의 기능적으로 로그인이나 결제와 같은 하나 또는 연속된 화면의에 상응하는 기능적으로 분리된 부분
- 앱에 하단 앱바가 있다면 각 목적지가 하나의 feature로 볼 수 있다.
- 