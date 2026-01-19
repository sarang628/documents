# [Domain Layer](https://developer.android.com/topic/architecture/domain-layer)
- UILayer와 DataLayer 사이의 옵션 레이어
- 복잡하거나 간단한 비지니스 로직을 캡슐화
- 뷰모델에서 재활용 목적
- 클린 아키텍처의 도메인 레이어와 다른 개념 주의
- 장점
  - 코드 중복 회피
  - 도메인 레이어를 사용하는 클래스 가독성 향상
  - 책임을 나눠 클래스가 커지는것을 방

## [네이밍 컨벤션](https://developer.android.com/topic/architecture/domain-layer#conventions)
- noun + UseCase
- ex) LogOutUserUseCase, MakeLoginRequestUseCase

## [의존성](https://developer.android.com/topic/architecture/domain-layer#dependencies)
- usecase 는 viewmodel과 repository 사이에 위치
- usecase는 repository에 의존성이 있음
- 재사용 가능한 로직으로 여러 repository와 다른 usecase도 포함할 수 있다.

## [코틀린에서 호출](https://developer.android.com/topic/architecture/domain-layer#use-cases-kotlin)
- 클래스 인스턴스를 호출할 수 있게 해주는 invoke() 함수를 사용할 수 있다. 

## [라이프사이클](https://developer.android.com/topic/architecture/domain-layer#lifecycle)
- usecase는 라이프사이클이 없음
- usecase를 사용하는 클래스로 scoped 됨.
- usecase는 mutable 데이터를 가지고 있으면 안됨.
- 의존하는 곳에 데이터를 넘기는 용도로 Usecase를 생성해 호출한다.

## [쓰레딩](https://developer.android.com/topic/architecture/domain-layer#threading)
- usecase는 main-safe 해야함.
- 오랫동안 blocking 하는 로직이라면 적절한 다른 쓰레드를 사용해야 함.
- 다른 레이어에 위치해야하는지도 고려 해야함
- 일반적으로 복잡한 계산은 재사용과 캐싱을 위해 데이터레이어에 위치 하도록 권장.
- 