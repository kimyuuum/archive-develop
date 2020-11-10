# Procedual vs OOP

### 절차지향

순차적인 처리가 main → 프로그램 전체가 유기적으로 연결되도록 만드는 프로그래밍 기법이다.

ex ) C, C++

- 객체 지향 언어보다 더 기계와 처리 방식이 유사하다.
- 코드의 순서가 바뀌면, 실행 순서가 정해져 있으므로 동일 결과 보장이 어렵다.

### 객체 지향

data와 절차를 하나의 덩어리로 묶어서 생각한다.

특성

1. 캡슐화

    private 접근자 등을 이용해서 외부에서의 접근을 원치 않는 data나 기능들을 보호 가능하다. information hiding이 가능하다. 낮은 결합도로, 의존성을 줄일 수 있다.

2. 추상화

    공통 기능들을 묶어서 하나의 클래스로 만드는 것 이다. 재사용성을 올릴 수 있고, 추상화를 통해 다형성이 나타난다.

3. 상속

    한 class를 상속받은 경우 해당 class에 있는 method를 그대로 사용하거나, 확장 가능하다. 재사용이 가능함.

4. 다형성

    @Override를 하며 생기는 특성이다. method의 이름은 같으나 파라미터나 리턴 타입이 달라 여러 기능들을 기대할 수 있다.

→ 코드의 재사용 및 확장이 용이하다.

처리 속도는 절차 지향보다 느리다.

절차 지향은 순차 실행에 초점이 맞춰져 있고, 객체 지향은 객체 사이의 관계 / 조직에 초점을 두고 있다.