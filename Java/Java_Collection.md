# Java Collection

데이터의 집합 그룹. 자료구조인 컬렉션과, 이를 구현하는 클래스를 정의하는 인터페이스를 제공한다.

### Collection을 사용하는 이유

다수의 데이터를 다루는데 표준화된 클래스들을 제공하기 때문에 DataStructure를 직접 구현하지 않고 편하게 사용 가능하다. 배열과 다르게, 객체를 보관하기 위한 공간을 미리 지정하지 않아도 된다. 상황에 따라 객체의 수를 동적으로 할당할 수 있다. ⇒ 공간적 효율성도 높인다.

### **Collection Interface**

모든 컬렉션의 상위 Interface. 모든 컬렉션의 핵심 메소드를 선언한다.



![image](https://user-images.githubusercontent.com/46887352/98635501-74ea1180-2368-11eb-91e4-0b44051e43ea.png)



### Interface

### SET

**Hash set**

**Tree set**

**순서를 유지하지 않는 Data의 집합이다. 중복을 허용하지 않는다**.

Hash set은 순서 예측이 불가능하고, 가장 빠른 임의의 접근 속도를 가진다.

### MAP

**Hash Table**

**Hash Map**

**Tree Map**

key / value 쌍으로 이루어진 data의 집합이다. 순서는 없고, key는 중복이 불가능하다. value는 중복 가능하다.

### Queue

**Linked List**

**Priority Queue** 

List와 유사하다.

### List

**Linked list**

**Vector**

**Array list**

순서가 있는 data의 집합. 중복을 허용한다.

- Linked list

    양방향 포인터 구조이다. 삽입,삭제시 data가 가리키고 있는 위치 정보만 수정하면 되어서 유용하다.

    stack dequeue, queue등 구현 가능하다.

- Vector

    동기화를 보장하는, 순서가 있는 List 구조 중 하나이다. 과거에 대용량 처리를 위해 사용했었다.

- Array List

    단방향 포인터 구조이다. 각 데이터에 대한 인덱스를 가지고 있어서, 조회 성능이 좋다. 동기화를 보장하지 않는다.

- Hash Table

    Hash Map보다는 느리지만 동기화를 지원한다. Null이 불가능하다. 멀티쓰레드 환경에서 유용하다.

- Hash Map

    동기화를 보장하지 않기 때문에 싱글 스레드 환경에서 훨씬 빠른 속도를 가지고 있다.

- Tree Map

    정렬되어서 key- value가 저장된다.

### HashMap vs HashTable

둘 다 Map Interface를 상속받아 구현된다.

**차이점**

1. 동기화

    HashMap은 동기화 지원을 하지 않는다. **Hash Table은 multiThread 환경에서 동기화를 지원**하므로, 구분해서 사용 가능하다. 속도는 HashMap이 더 빠르다.

2. Table은 null을 허용하지 않고, map은 null도 허용한다.

### Concurrent HashMap

HashMap을 thread safe하게 만든다. key / value null을 허용하지 않는다.

### Vector vs ArrayList

배열을 클래스로 구현해서, 데이터를 추가하면 자동으로 memory 공간이 늘어난다. 인덱스를 통한 접근이 가능하고, 순서가 존재하며 Data의 중복이 가능하다.

동기화 여부로 큰 차이점을 들 수 있다. vector는 자동적으로 내부 동기화가 이루어져 multi thread 환경에서 안정적이지만 성능이 느리다.