프로젝트의 하위 모듈이 old 라이브러리를 의존해서 문제가 생기는 경우

```
gradle :app:dependencyInsight \
  --dependency 모듈명 \
  --configuration debugRuntimeClasspath

```