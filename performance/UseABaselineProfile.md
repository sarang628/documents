# [Use a baseline profile](https://developer.android.com/develop/ui/compose/performance/baseline-profiles)
- interpretation 과 just-in-time (JIT) compilation을 건너뜀
- 실행속도 30% 향상
- 앱이나 라이브러리에 Baseline Profile을 포함해 배포
- ART가 AOT를 통해 코드 경로 최적화
- 새로 업데이트나 설치된 앱에 퍼포먼스 강화
- PGO가 엡의 시작을 최적화, jank 제거, 전반적 런타임 퍼포먼스 향상.

## [Compose 퍼포먼스 고려사항](https://developer.android.com/develop/ui/compose/performance/baseline-profiles#considerations)
- 컴포즈는 플랫폼에 일부가 아닌 라이브러리로 제공
- 이는 다양한 안드로이드 버전을 더 자주 지원 가능
- 대신 라이브러리 로드 비용이 비쌈
- 앱 실행 시 라이브러리가 필요할 때 로드하기 때문에 앱의 시작을 느리게 함

## [baseline profile의 장점](https://developer.android.com/develop/ui/compose/performance/baseline-profiles#benefits)
- 중요한 함수와 클래스를 정의하여, APK AAB와 함께 배포됨
- 앱 설치시 이 코드들을 컴파일하여 앱 실행시 바로 사용할 수 있도록 해줌

### [Macrobenchmark](https://developer.android.com/develop/ui/compose/performance/baseline-profiles#macrobenchmark)
- macrobenchmark을 사용하는 baseline profile을 설치하면 사용자의 여정을 커버
- profile 설정 후 도움이 되는지 확인을 위한 테스트 필요
- Macrobenchmark 테스트를 작성, aseline Profile을 작성·수정하면서 테스트 결과를 확인