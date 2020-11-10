# JAR / WAR

둘 다 압축 파일의 유형이다.

애플리케이션 소스들을 배포할때에, path 등의 설정으로 인한 이슈를 제거하기 위해 탄생한 압축 방식이다. 압축의 해제 없이 JDK에서 각 파일들을 접근하여 사용한다.

## JAR (Java Archive)

하나의 애플리케이션 기능이 가능하도록 java 파일 등을 압축하고, 지원한다. path 등의 경로를 유지하기 때문에 배포된 jar 파일을 사용하는 사용자들은 각 파일들에 대한 path 문제에서 벗어날 수 있다.

## WAR (Web Archive)

자바 기반 웹 프로젝트의 최종 결과 포맷. 웹 어플리케이션을 지원하기 위한 압축방식이다.

배포를 위한 최소 단위이며, WAS마다 조금씩 설정이나 방식이 다르지만 war파일의 규격은 동일하다. 

jsp, servlet, git, html, jar등을 압축하고 지원한다. 

war로 올리면 was가 압축을 해제하여 배포한다. war는 단독 실행이 불가능하다. **서버 컨테이너 WAS 에 의해서 실행되어야 한다**. 따라서 배포에 대한 정보가 web.xml에 있다.

### 차이점

jar는 실행된 클래스(main)를 명시하며, JVM 위에서 단독으로 수행 가능하다. war는 단독 실행이 불가능하다. 서버 컨테이너에 의해서 실행되어야 하고, 배포에 대한 meta 정보를 담고 있다.