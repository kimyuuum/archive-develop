# Overriding / Overloading

### Overriding

**상속** 관계의 클래스간에 같은 이름의 method를 정의한다. 

1. 오버라이드하고자 하는 method가 상위 클래스에 존재해야 한다.
2. 메소드 이름이 같아야 한다.
3. return type / parameter 형태도 같아야 한다.
4. **상위 메소드와 내용이 동일하거나, 추가되어야 한다.**

    **다형성** 중 하나.

### Overloading

함수의 이름이 같으나, return type이나 받는 매개변수가 다른 경우이다. 한 클래스 내에 여러개의 이름이 같은 method를 정의 가능하다.

1. method 이름이 같다
2. return type은 같아도/달라도 된다.
3. parameter 개수가 달라야 한다.
4. parameter 개수가 같을 경우, data type이 달라야 한다.