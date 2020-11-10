# Class / Object / Instance

### Class

객체를 만들어내기 위한 설계도 / 틀을 말한다. 연관 되어있는 변수와 메서드의 집합이다.

### Object

SW에 구현할 대상. 클래스에 선언된 모양 그대로 생성된 실체.

class의 instance라고도 한다. 

모든 Instance를 대표하는 포괄적 의미를 가진다.

### Instance

SW에 구현된 구체적 실체이다. 객체를 SW에 실체화한것.

→ 메모리에 할당된다.

인스턴스는 객체에 포함된다. OOP의 관점에서, 객체가 메모리에 할당되어 실제 사용되는 것이 인스턴스이다. 실체화된 오브젝트(인스턴스)가 메모리에 할당되는것이다.

객체는 클래스의 인스턴스이다. → 어떤 원본으로부터 '생성된 복제본'

```java
public class Animal{...} // Class

public class Main{
	public static void main(String[] args){
		Animal cat,dog; // 객체 Object
		
		cat = new Animal();
		dog = new Animal();   
		//cat, dog = 메모리를 할당 받은 animal class의 인스턴스.
	}
}
```