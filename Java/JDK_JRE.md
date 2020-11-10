# JDK / JRE



JDK = JRE + @
JRE = 읽기 전용, JDK = 읽기 + 쓰기 전용

### JVM (Java Virtual Machine)

JVM은 자바 소스코드부터 만들어지는 바이너리 파일(.class)를 실행 가능하다. 

플랫폼 의존적이다. → 리눅스 JVM과 Windows JVM은 다르다.

컴파일된 바이너리 코드는 어느 JVM에서도 동작시킬 수 있다.

- 역할

    바이너리 코드를 읽는다 → 검증한다 → 실행한다

<img src="/Users/kim-yumin/Library/Application Support/typora-user-images/image-20201110151939006.png" alt="image-20201110151939006" style="zoom:67%;" />

### JRE (Java Runtime Environment)

컴파일된 자바 프로그램을 실행시킬 수 있는 자바 환경. JRE에 JVM이 자바 프로그램을 동작 시킬 때 필요한 파일들이 있다. Java Program을 실행시키려면 JRE는 필수이다.

Java Programming 도구는 포함이 되어있지 않아서, JDK가 필요하다.

### JDK (Java Development Kit)

자바 프로그래밍 시 필요한 컴파일러 등이 포함되어있다. 개발을 위해 필요한 도구 (Javac, java)를 포함한다.

**JDK를 설치하면, JRE도 같이 설치된다.**