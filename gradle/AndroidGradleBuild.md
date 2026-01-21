# [Gradle build overview](https://developer.android.com/build/gradle-build-overview)

안드로이드 앱은 일반적으로 Gradle을 사용해 빌드.

## [빌드는 무엇인가? (What is a build?)](https://developer.android.com/build/gradle-build-overview#is-build?)

- 빌드는 작성한 코드를 실행 가능한 앱으로 만드는 것.
- 빌드는 다양한 도구, 분석, 컴파일, 패키지 앱 및 라이브러리 등을 포함.
- Gradle은 **task 기반**으로 명령어를 실행 위 작업들을 수행.
- Task는 입력을 출력으로 만드는 **캡슐화된 명령어**
- Plugin은 이 Task를 정의 및 구성 한다.
- Plugin을 적용하는것은 이 task들을 등록하고 이 task의 입출력을 사용하여 서로를 연결하는 것이다.
- AGP(Android Gradle Plugin)을 적용하는 것은 APK 또는 라이브러리를 만들기 위한 필요한 모든 Task들을 등록하는 것.
- Plugin은 convention을 선호함으로 잘 설정된 기본값(default value)을 제공한다.
- DSL(Domain-Specific Language)을 이용해서 추가적인 정의를 할 수 있다.
- DSL은 의미 설계되어 있기때문에 **어떻게 빌드**할지 보다 **무엇을 빌드** 할지 명시할 수 있다.
- (Plugin의 Login에서 how를 관리)
- Task의 input은 파일, 디렉토리 또한 Java 타입들로 인코딩된 정보가 될 수 있다.
- Task의 output은 오직 파일, 디렉토리 이다.
- Task의 output를 다른 task의 input으로 넣을 수도 있다.(task의 연결(link))
- Gradle은 임의의 코드를 작성할 수 있지만 복잡해지면 유지보수하기 힘들어짐
- 플러그인은 유닛테스트도 가능하기 때문에 빌드 로직은 플러그인에서 작성하기
- gradle은 어떻게(how)가 아닌 무엇(what)을 할 것인지만 작성

## [Gradle 빌드하면 일어나는 일?](https://developer.android.com/build/gradle-build-overview?utm_source=android-studio-app&utm_medium=app#happens-when)
- 3가지 구문 실행
- Initialization
  - 어떤 프로젝트과 하위 프로젝트가 포함되었는지 확인.
  - 위의 빌드파일과 적용된 플러그인에 대한 classpath를 만듬(gradle은 JVM 에서 실행됨.)
  - settings 파일을 중심으로, 어떤 프로젝트들을 빌드할지와 플러그인, 라이브러리를 어디에서 가져올지를 정의.
- Configuration
  - 각 프로젝트의 태스크를 등록하고 빌드 파일을 실행
- Execution
  - Configuration의 결과로 모든 빌드 단계를 나타내는 Task의 DAG(Directed Acyclic Graph) 생성

## [DSL 설정](https://developer.android.com/build/gradle-build-overview?utm_source=android-studio-app&utm_medium=app#configuration-dsls)
- DLS은 선언형 으로 데이터에 specifying 초점을 둘 수 있게 해준다.
- 각 블럭은 설정 함수와 속성들로 구성되어있다.

## [외부 의존성](https://developer.android.com/build/gradle-build-overview?utm_source=android-studio-app&utm_medium=app#external-dependencies)
- 메이븐 Artifacts는 group:artifact:version 으로 identity를 갖음.
- 빌드 관리를 하는데 상당한 역할을 한 기능
- 프로젝트를 작은 단위로 나눠 관리가 가능, 각 모듈을 isolating 함으로써 빌드 속도 향상을 가져올 수 있음.

## [빌드 변수](https://developer.android.com/build/gradle-build-overview?utm_source=android-studio-app&utm_medium=app#build-variants)
- build types과 product flavors로 구성
- build type
  - debug : 빠른 빌드, 디버깅 가능한 설정
  - release: 코드 최소화, 보호, 실제 설치용
- product flavors
  - 데모, 풀버전, 무료 유료 등의 다양한 환경에 맞게 추가 가능