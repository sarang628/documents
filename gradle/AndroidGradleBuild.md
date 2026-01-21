# [Gradle build overview](https://developer.android.com/build/gradle-build-overview)

안드로이드 앱은 일반적으로 Gradle을 사용해 빌드.

## [빌드는 무엇인가? (What is a build?)](https://developer.android.com/build/gradle-build-overview#is-build?)

빌드는 작성한 코드를 실행 가능한 앱으로 만드는 것.
빌드는 다양한 도구, 분석, 컴파일, 패키지 앱 및 라이브러리 등을 포함.
Gradle은 task 기반으로 명령어를 실행 위 작업들을 수행.

Task는 입력을 출력으로 만드는 **캡슐화된 명령어**

Plugin은 이 Task를 정의 및 구성 한다.

Plugin을 적용하는것은 이 task들을 등록하고 이 task의 입출력을 사용하여 서로를 연결하는 것이다.

AGP(Android Gradle Plugin)을 적용하는 것은 APK 또는 라이브러리를 만들기 위한 필요한 모든 Task들을 등록하는 것.

Plugin은 convention을 선호함으로 잘 설정된 기본값(default value)을 제공한다.
DSL(Domain-Specific Language)을 이용해서 추가적인 정의를 할 수 있다.

DSL은 의미 설계되어 있기때문에 **어떻게 빌드**할지 보다 **무엇을 빌드** 할지 명시할 수 있다.

(Plugin의 Login에서 how를 관리)


Task의 input은 파일, 디렉토리 또한 Java 타입들로 인코딩된 정보가 될 수 있다.
Task의 output은 오직 파일, 디렉토리 이다.
Task의 output를 다른 task의 input으로 넣을 수도 있다.(task의 연결(link))


TODO:: 아래 문장 이해해기!

While Gradle supports writing arbitrary code and task declarations in your build files, this can make it more difficult for tooling to understand your build and for you to maintain. For example, you can write tests for code inside plugins but not in build files. Instead, you should restrict build logic and task declarations to plugins (that you or someone else define) and declare how you want to use that logic in your build files.