# [Guide to Android app modularization](https://developer.android.com/topic/modularization?_gl=1*1wbxt64*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDA2NDAkbzEkZzAkdDE3NzIwMDA2NTgkajQyJGwwJGg3MTQ1MDQ4NjU.)
- 다중 gradle 모듈은 multi-module 프로젝트로 알려져있다.

## [The growing codebase problem](https://developer.android.com/topic/modularization?_gl=1*1wbxt64*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDA2NDAkbzEkZzAkdDE3NzIwMDA2NTgkajQyJGwwJGg3MTQ1MDQ4NjU.#growing-codebase)
- 코드베이스가 커짐에 따라, 확장성, 가독성, 그리고 전반적인 코드 품질이 나빠지곤 한다
- 유지보수자가 쉽게 유지보수 가능한 구조를 강화하는 구현일 하지 않았기 때문
- 모듈화는 이런 문제를 해결하고 유지보수를 강화하기 위한 코드베이스를 구조화하는 수단


## [What is modularization?](https://developer.android.com/topic/modularization?_gl=1*1wbxt64*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDA2NDAkbzEkZzAkdDE3NzIwMDA2NTgkajQyJGwwJGg3MTQ1MDQ4NjU.#what-is-modularization)
- 모듈화는 코드베이스를 느슨하게 결합하고 스스로 필요한 것을 모두 갖춘 part(부품)로 나누는 것
- 각 part는 모듈이다.
- 각 모듈은 독립적이며, 명확한 목적을 서비스 한다.
- 큰 시스템에 설계와 관리의 복잡성을 줄이기위해 큰 문제를 작은 하위 문제로 나눔으로써 해결한다.

## [Benefits of modularization](https://developer.android.com/topic/modularization?_gl=1*1wbxt64*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDA2NDAkbzEkZzAkdDE3NzIwMDA2NTgkajQyJGwwJGg3MTQ1MDQ4NjU.#benefits)
- 모듈화의 장점은 많지만, 코드베이스의 유지보수와 코드 품질의 향상에 초점을 둔다.
- 모듈화된 코드베이스로 얻을 수 있는 장점
  - 재사용성 : 다양한 앱에 코드를 공유 할 수 있음
    - 모듈들은 효율적인 building blocks
    - 앱은 features의 합이고, features는 모듈을 분리해서 구성됨.
    - 특정 모듈의 기능은 어떤 앱에서는 활성되거나 그렇지 않을 수 있다.
    - :feature:news은 full 버전에서는 사용되나 demo에선 사용되지 않을 수 있다.
  - Strict visibility control :모듈화는 코드베이스의 다른 part에 무엇을 노출시킬지 쉽게 결정할 수 있게 해준다.
    - public, internal, private등을 사용
  - Customizable delivery : Play Feature Delivery 앱의 특정 feature에 조건 또는 요청에 따라 전달할 수 있게 앱 번들의 향상된 기능을 사용한다.
- 다른 기술이지만 모듈화로 도움이 될 수 있는 장점
  - Scalability : 강하게 결합되어있는 코드베이스는 하나의 변경이 관련없는 부분까지 영향을 미칠 수 있음
    - 적절하게 모듈화된 코드는 separate of concern 이론이 적용되어 결합을 제한.
    - 이는 기여자들에게 더 큰 자율성을 부여
  - Ownership : 자율성을 부여함과 더불어 책임감을 부여할 수 있다.
    - 모듈은 코드를 유지보수하는 한명의 기여자를 배정할 수 있다.
  - Encapsulation : 캡슐화의 의미는 각 part들이 다른파트의 knowledge를 가능한 적게 알고 있어야 한다.
    - 고립된 코드는 쉽게 읽고 이해할 수 있다.
  - Testability : 
  - Build time : incremental build, build cache or parallel build 와 같은 어떤 Gradle 기능은 빌드 성능 향상하는 모듈화를 돕는다.

## [Common pitfalls](https://developer.android.com/topic/modularization?_gl=1*1wbxt64*_up*MQ..*_ga*MTg3MDAxMjQ3Ni4xNzcyMDAwNjQx*_ga_6HH9YJMN9M*czE3NzIwMDA2NDAkbzEkZzAkdDE3NzIwMDA2NTgkajQyJGwwJGg3MTQ1MDQ4NjU.#common-pitfalls)
- 