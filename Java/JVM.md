# JVM

![image](https://user-images.githubusercontent.com/46887352/98635263-0016d780-2368-11eb-8c98-76a37124d3b4.png)



### 클래스 로더 시스템

`.class` 에서 byte code를 읽고, 메모리에 저장한다.

1. class를 읽어온다
2. 레퍼런스를 연결한다.
3. static 값들을 초기화 및 변수에 할당한다.



### Memory

- stack

    각 thread마다 독립적으로 가지는 영역. 지역 변수 등이 해당된다.

- PC Register

    Thread의 context switching이 일어날 경우 현재 작업하던 address 정보를 기록한다.

- Heap

    객체를 저장 및 공유한다. (인스턴스)

- Method

    클래스 수준의 정보(클래스 이름, 부모클래스 이름, 메소드, 변수)를 저장한다.

    다른 Thread와 공유한다.

- Native Method Stack

    실제 실행 가능한 기계어로 작성된 프로그램을 실행하는 영역.
    
    

### 실행 영역

- Interpreter

    Byte code를 기계가 이해 가능하게 native code로 변환한다.

- JIT(Just In Time) 컴파일러

    인터프리터가 반복되는 코드를 발견하면, 반복되는 code는 모두 native code로 바꾼다.