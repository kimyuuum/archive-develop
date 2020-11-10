# Interface / Abstract Class

### 공통점

추상 클래스와 Interface는 선언만 있고, 구현 내용이 없다. 이 자체를 이용해서 새로운 인스턴스 생성은 불가능하다.

Abstract class(추상)은 extends로 상속받아 구현하거나, Interface를 implements하고 구현한 자식 클래스가 객체 생성이 가능하다.

### 차이점

### Abstract Class(추상 클래스)

추상 메소드(abstract method)가 하나라도 존재하는 클래스. 일부는 구현된 method, 일부는 abstract method가 존재할 수 있다. ⇒ 추상화 시킬 때 사용하자. is-a관계이다.

**여러 클래스의 공통점을 찾아서 구현할 때에  사용하자.**

Dog is-a Animal / Cat is-a Animal

Animal이라는 추상 클래스로 추상화시키면 된다.

상속으로 기능을 확장시킬 경우 사용하자. 다중 상속은 불가능하다. 

멤버 변수나 구현 메서드는 존재 가능하다.

### Interface(인터페이스)

implements하는 특정 클래스의 모든 method를 반드시 정의하도록 강제한다. 구현 객체가 같은 동작을 한다는 것을 보장하고, 다중 상속도 가능하다.

Interface에 명시된 추상 메서드는 모두 구현해야 한다. 아니면 컴파일 에러가 발생한다.

사용하는 이유 → 다형성

### 다형성?

상속받은 class 또는 인터페이스의 method를 재정의하여 서로 다른 행동을 만들 수 있다.