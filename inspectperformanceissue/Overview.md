# [Profile your app performance](https://developer.android.com/studio/profile?_gl=1*olerw8*_up*MQ..*_ga*MTM4MTY5Nzc4MS4xNzY5MTI3MzIx*_ga_6HH9YJMN9M*czE3NjkxMjczMjEkbzEkZzAkdDE3NjkxMjczMjEkajYwJGwwJGgyODE1NzE4OTA.)
- poor 성능
  - 느린응답, 끊김이 심한 애니메이션(choppy animations), 멈춤(freezes), 과한 소비 전력
- profiling을 포함시켜 성능개선

# [요구사항](https://developer.android.com/studio/profile?_gl=1*olerw8*_up*MQ..*_ga*MTM4MTY5Nzc4MS4xNzY5MTI3MzIx*_ga_6HH9YJMN9M*czE3NjkxMjczMjEkbzEkZzAkdDE3NjkxMjczMjEkajYwJGwwJGgyODE1NzE4OTA.#requirements)
- build variant에 profileable을 추가
- Android Manifest 파일에 <profileable android:shell="true" /> 추가
- Gradle 7.3 이상, API level 29 이상, 구글플레이 포함하고 있어야 함.

# [Profileable debuggable 앱](https://developer.android.com/studio/profile?_gl=1*olerw8*_up*MQ..*_ga*MTM4MTY5Nzc4MS4xNzY5MTI3MzIx*_ga_6HH9YJMN9M*czE3NjkxMjczMjEkbzEkZzAkdDE3NjkxMjczMjEkajYwJGwwJGgyODE1NzE4OTA.#profileable-v-debuggable)
- 디버그 모드로 하면
  - 자바/코틀린 할당 기록, 메모리 덤프, Interaction timeline(API 26 이상)을 할 수 있다.
    - Interaction timeline : user interaction과 app lifecycle event를 테스크 뷰에서 볼 수 있음.
- 하지만 프로필 앱은 기본적으로 release모드를 위한 것 (debug모드 자체만으로 성능 비용이 나감)
- 안드로이드 앱 빌드 메뉴에
  - Profile 'app' with low overhead : 프로필 모드를 위한 옵션
  - Profile 'app' with complete data : 디버그 모드를 위한 옵션