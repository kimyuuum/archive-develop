# Spring Boot vs Spring MVC

### Dependency의 차이

버전까지 명시해야 했던 것에 비해, 길이가 짧아지고 권장 버전으로 자동 설정을 해준다.

starter 시리즈로 알아서 기본 의존성도 설정한다.

### Configuration

단순 application.properties, yaml을 사용하여 입맛에 맞게 환경 설정을 편리하고 간단하게 할 수 있다. yaml file을 사용하면, 사용자에게 친화적이다. depth를 이용하는 방식이기 때문에 보기에도 편하다.

### Embedded Server

서버 구동 시간이 절반 가까이 단축된다. 내장 servlet container로 jar file도 간단하게 배포가 가능하다.

하지만 Embedded 컨테이너에서 실행하기에 규모가 큰 프로젝트는 MVC로 WAS 배포하는 형태가 더 안정적이다.