# Design Pattern



SW 설계 시, 특정 맥락에서 자주 발생하는 고질적인 문제들이 또 발생했을 때에 재사용 가능하다.

### 구조

Context - 문제가 발생하는 여러 상황을 기술한다. ⇒ 패턴이 적용될 수 있는 상황

Problem - 패턴이 적용되어 해결될 필요가 있는 여러 design issue를 기술한다.

Solution - 문제를 해결하도록 설계를 구성하는 요소들과, 그 요소들 사이의 관계, 책임, 협력 관계를 기술한다.



## Singleton Pattern

애플리케이션에서 인스턴스를 하나만 만들어서 사용하기 위한 패턴이다. Connection / Thread Pool이 여러개가 필요 없어서 자원의 효율성이 좋다. 

### 구현

Instance 생성에 제약을 걸어둔다.

`new`를 실행할 수 없게 private 접근 제어자를 지정하고, 유일 단일 객체를 위해 정적 메소드를 지원해야한다.

```java
public class Singleton{

	private static Singleton SingletonObject;
	private singleton(){}

	public static singleton getInstance(){  //하지만 여기에 동시접근할 경우 싱글톤해침.
		if(singletonObject == null){
			singletonObject = new Singleton();
		}
		return SingletonObject;
	}

}
```

```java
public class Singleton{
	private static volatile Singleton singletonObject = new Singleton();
	
	private Singleton(){}
	public static Singleton getSingletonObject(){
		return singletonObject;
	}
}
```

⇒ 클래스가 생성되는 시점에 미리 객체를 생성해두고, return 하자.

`volatile` : 컴파일러가 특정 변수에 대해 옵티마이저가 캐싱을 적용하지 못하도록 하는 키워드.