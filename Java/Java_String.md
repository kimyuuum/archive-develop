# Java String

> String, StringBuffer, StringBuilder ⇒ Java에서 문자열을 관리하고 저장하는 class.

### 차이점

String = immutable

StringBuffer, StringBuilder = mutable

## String

연산이 적고 조회가 많은 multi thread에서 사용하자.

String은 new 연산을 통해서 생성되면, **인스턴스**의 메모리 공간은 절대 변하지 않는다. +연산이나, concat을 이용해도 memory 공간이 변하는 것이 아니라, 새로운 string 객체를 new로 만들어서 새로 메모리 공간을 할당한다.

단점

이렇게 새로운 메모리가 계속 생기면, 기존 문자열은 GC에 의해 제거되어야 한다. 또한 객체를 만드는 오버헤드가 발생해서 성능이 떨어진다.

장점

String객체는 불변하기 때문에 단순 조회 연산에서는 타 클래스보다 훨씬 빠르다.

multithread 환경에서 동기화를 신경쓰지 않아도 된다.

## StringBuffer / StringBuilder

String과 다르게 mutable하다. 

문자열 연산 → class를 한번 생성한다(new) → 연산 시 필요 크기에 맞춰 문자열을 변경한다.

문자열 연산이 자주 있을 때에 사용하자. 둘의 클래스 method가 같아서 호환도 가능하다.

차이점

String Buffer는 multithread 환경에서 synchronized 키워드가 가능하므로 **동기화가 가능하다. (thread - safe)**

String Builder는 동기화를 지원하지 않는다. 싱글 스레드 환경에서 연산 처리가 빠르다.

### '==' / .equals()

`'=='`는 주소값을 비교한다. (reference comparison)

'==' operator compares the value of two object references.

`.equals()` 는 값을 비교한다.

Evaluates to the comparison of values int the objects value inside string instances. (on the heap)

### 1. New 연산자 이용하기

`new` 를 사용하면 Heap 영역에 할당된다. 같은 문자열이더라도, 다른 객체로 개별적 존재가 가능하다.

`String str = new String("test");`

### 2. Literal 이용하기

`String str = "Hello";`

String constant pool에 할당된다. 우선 constant pool에 있는지 검사하고, 있으면 해당 주소를 return한다. 아니면 새로운 주소를 return 한다.