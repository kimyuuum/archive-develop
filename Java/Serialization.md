# Serialization



정보를 대상 시스템에 복원 가능하게 전달하기 위해서, 다른 형태 (Json, XML, TEXT)로 변경하는 행위.

Java는 객체지향 언어이다. 가상 머신 내에 존재하는 것은, 객체들로 이루어져 있다. Serialization Interface를 통해서 직렬화를 구현한다.



### 객체 직렬화 개념

Java I/O 처리는 정수, 문자열, 바이트 단위의 처리만 지원한다. 복잡한 객체의 내용을 저장하거나 복원, 네트워크 전송을 하려면 각 내용을 일정한 형식(=패킷)으로 만들어서 전송해야 한다.

객체의 내용(멤버 변수의 내용)을 자바 I/O가 자동적으로 바이트 단위로 변환하여 저장,복원,전송 가능한 기능을 제공해준다.

객체 직렬화를 처음 시작한 객체를 중심으로 트리 구조의 객체 직렬화가 연속적으로 일어난다.



### RMI (Remote Method Invocation)

한쪽의 JVM에 존재하는 객체가 네트워크를 통해 다른곳의 JVM에 존재하는 객체의 메소드를 호출할 수 있게 해준다. Java는 **분산 환경에서 분산된 컴퓨터간에 정보를 주고받을 수 있게 하기 위해 RMI를 지원**한다.

원격 프로시저 호출 ( Remote Procedure Call ) 이라고 불린다.

RMI를 사용하려면 객체를 네트워크로 전송 가능한 형태로 바꿔야 한다. ⇒ **직렬화/역직렬화를 사용하자**.



### 객체 직렬화 과정

- 직렬화

    writeObject() 메소드에 자신을 넘기며 직렬화된다. 

    객체(private field, super class 상속 필드)를 기록한다.

- 직렬화 해제

    readObject() 메소드를 호출해서 스트림으로부터 읽어들인 값을 직렬화 되기전의 객체로 다시 만들게 된다.



### Interface Serializable

객체 직렬화가 필요한 객체는 Serializable Interface를 구현해야 한다. Serializable Interface는, 객체가 직렬화 제공이 되어야 함을 JVM에 알려주는 Interface이다.

file / network에 스트림을 생성하고, 객체를 보낼 수 있는 스트림으로 변환한다. (= 직렬화)

1. network / file에 스트림 생성
2. 생성 스트림 → Object Stream으로 변환
3. 입력 스트림 : ObjectInputStream

    출력 스트림 : ObjectOutputStream

4. 직렬화된 객체를 객체 스트림을 통해 전송한다. (WriteObject())
5. 객체 스트림을 통해서 직렬화된 객체를 받는다. 역직렬화를 위해서 ReadObject()를 사용한다.



### Transient / Static

직렬화 후 보존하고 싶지 않은 멤버 변수 → `transient string password;` 와 같은 형식으로 선언한다. static 선언 변수도 공유 메모리를 사용하므로, 직렬화 할 때 제외된다.