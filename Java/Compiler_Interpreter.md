# Compiler / Interpreter

컴파일러는 전체 소스코드를 보고 명령어를 수집하고 재구성한다. 인터프리터는, 소스코드의 각 행을 연속적으로 분석하며 실행한다.

Compiler : high ——> low level (기계어)로 바로 번역한다.      ex ) C,C++

Interpreter : high ——> Intermediate ——> low. 중간 단계가 존재한다.    ex) Python

Java는 컴파일러와 인터프리터 둘 다 가지고 있다.

### Java Compiler

Java의 Compiler는, 우선 소스코드를 .class파일 형식의 바이트 코드로 변환한다. compiler의 정의 자체는 '기계어'라는 정의를 가지고 있다고 해서 무조건 low level의 언어로 번역하는 것이 아니다. JVM에 올라가기 위해 compiler를 사용하는데, JVM도 일종의 기계이기 때문에 컴파일러를 사용한다.

### Java Interpreter

.class 파일의 바이트 코드를 완전한 기계어로 번역한다. 이 때 기계는 사용자가 직접 사용하는 환경이라고 볼 수 있다.