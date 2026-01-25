# [안드로이드에서 공통 코틀린 패턴 사용하기](https://developer.android.com/kotlin/common-patterns?_gl=1*1mfh22*_up*MQ..*_ga*MjA5MDI2ODYwNi4xNzY4NTQxNjEx*_ga_6HH9YJMN9M*czE3Njg1NDE2MTAkbzEkZzAkdDE3Njg1NDE2MTAkajYwJGwwJGgxMDQ0NDM4NjU3)

## [상속](https://developer.android.com/kotlin/common-patterns?_gl=1*1mfh22*_up*MQ..*_ga*MjA5MDI2ODYwNi4xNzY4NTQxNjEx*_ga_6HH9YJMN9M*czE3Njg1NDE2MTAkbzEkZzAkdDE3Njg1NDE2MTAkajYwJGwwJGgxMDQ0NDM4NjU3#inheritance)
- 상속 오퍼레이터 '**:**'
- 자식 클래스는 super 클래스의 생성자를 호출해야한다.
- override 부모의 함수를 대신 쓸 수 있고 super()을 사용하여 부모를 참조할 수 있다.

## [Nullability 와 초기화](https://developer.android.com/kotlin/common-patterns?_gl=1*1mfh22*_up*MQ..*_ga*MjA5MDI2ODYwNi4xNzY4NTQxNjEx*_ga_6HH9YJMN9M*czE3Njg1NDE2MTAkbzEkZzAkdDE3Njg1NDE2MTAkajYwJGwwJGgxMDQ0NDM4NjU3#fragment-nullability)
- properties 선언 시 초기값을 반드시 지정해야 함
- 클래스의 instance 얻으면 어떤 값이든 접근이 가능해짐
- 개발을 하다보면 객체의 지연 생성이 필요함. lateinit을 사용하면 지연 생성 가능
  - Fragment의 View 객체는 Fragment#onCreateView 호출 전까지 생성이 되지 않는다.

## [SAM conversion](https://developer.android.com/kotlin/common-patterns?_gl=1*1mfh22*_up*MQ..*_ga*MjA5MDI2ODYwNi4xNzY4NTQxNjEx*_ga_6HH9YJMN9M*czE3Njg1NDE2MTAkbzEkZzAkdDE3Njg1NDE2MTAkajYwJGwwJGgxMDQ0NDM4NjU3&utm_source=android-studio-app&utm_medium=app#sam)
- 조건 : 하나의 abstract 함수만 갖는 인터페이스
- Single Abstract Method conversion
- 이를 적용하면 코드가 상당히 깔끔해진다

## [Companion objects](https://developer.android.com/kotlin/common-patterns?_gl=1*1mfh22*_up*MQ..*_ga*MjA5MDI2ODYwNi4xNzY4NTQxNjEx*_ga_6HH9YJMN9M*czE3Njg1NDE2MTAkbzEkZzAkdDE3Njg1NDE2MTAkajYwJGwwJGgxMDQ0NDM4NjU3&utm_source=android-studio-app&utm_medium=app#companion)
- 변수 또는 함수로 타입에 연결되있긴 하지만 특정 객체에 묶여있진 않음
- 자바의 static과 비슷함

## [Property delegation](https://developer.android.com/kotlin/common-patterns?_gl=1*1mfh22*_up*MQ..*_ga*MjA5MDI2ODYwNi4xNzY4NTQxNjEx*_ga_6HH9YJMN9M*czE3Njg1NDE2MTAkbzEkZzAkdDE3Njg1NDE2MTAkajYwJGwwJGgxMDQ0NDM4NjU3&utm_source=android-studio-app&utm_medium=app#delegate)
- 어떤 객체 초기화 시 같은 패턴이 긴 코드를 적용해야 하는 경우
- 선언 시 마다 긴 패턴의 코드가 중복으로 만들어지는 것을 간결하게 해줌
- ex) private val viewModel: LoginViewModel by viewModels()

## [Nullability](https://developer.android.com/kotlin/common-patterns?_gl=1*1mfh22*_up*MQ..*_ga*MjA5MDI2ODYwNi4xNzY4NTQxNjEx*_ga_6HH9YJMN9M*czE3Njg1NDE2MTAkbzEkZzAkdDE3Njg1NDE2MTAkajYwJGwwJGgxMDQ0NDM4NjU3&utm_source=android-studio-app&utm_medium=app#nullability)
- ? 사용

## [Interoperability](https://developer.android.com/kotlin/common-patterns?_gl=1*1mfh22*_up*MQ..*_ga*MjA5MDI2ODYwNi4xNzY4NTQxNjEx*_ga_6HH9YJMN9M*czE3Njg1NDE2MTAkbzEkZzAkdDE3Njg1NDE2MTAkajYwJGwwJGgxMDQ0NDM4NjU3&utm_source=android-studio-app&utm_medium=app#interop)
- 코틀린은 null safe를 처리할 수 있지만 Java는 그렇지 못함.
- 코틀린과 자바는 서로 호출 가능하기 떄문에 자바 호출 시 이 점 유의

## [Platform types](https://developer.android.com/kotlin/common-patterns?_gl=1*1mfh22*_up*MQ..*_ga*MjA5MDI2ODYwNi4xNzY4NTQxNjEx*_ga_6HH9YJMN9M*czE3Njg1NDE2MTAkbzEkZzAkdDE3Njg1NDE2MTAkajYwJGwwJGgxMDQ0NDM4NjU3&utm_source=android-studio-app&utm_medium=app#platform-types)
- 