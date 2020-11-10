# Java



객체 지향 프로그래밍 이란, 캡슐화 / 다형성 / 상속을 이용하여 코드 재사용을 증가시키고, 유지보수를 감소시키는 장점을 얻기 위해서 객체들을 연결 시켜 프로그래밍 하는 것 입니다.



### Java 접근 제어자

접근 제어자를 통해서 Encapsulation과 Information Hiding을 할 수 있다.

- Public - 모든 클래스에서 접근이 가능하다.
- Private - 동일 클래스 내에서만 접근 가능하다.
- Protected - 상속받은 클래스와 같은 패키지 내에 있는 클래스가 접근 가능하다.



### Java Try-with-Resource

try에서 선언된 객체들에 대해서, try가 종료될 때 자동으로 자원을 해제한다.

`try(...)` 에 객체 선언, 할당을 한다. try구문에서 사용 가능하다.  try를 벗어나면, close() method를 호출해서 finally에서 호출을 하지 않아도 된다.

```java
public static void main(String args[]){
	try(
		FileInputStream is = new FileInputStream("file.txt");
		BufferedInputStream bis = new BufferedInputStream(is);
	){
		int data = -1;
		while((data = bis.read()) != -1){
			System.out.print((char) data);
		}
	}catch (IOException e){
		e.printStackTrace();
	}
}
```

코드를 짧고 간결하게 하여 읽기 쉽고, 유지 보수가 쉬워진다.

AutoCloseable()를 구현해야 한다. → Java 7부터 지원한다.



### Synchronize?

동기화를 위해 대표적으로 Mutal Exclusion을 이용해서, 한 객체가 특정 Data를 사용중이라면, 다른 Thread는 접근 못하게 Lock 시킨다. method 앞에 synchronized를 붙여 동기화한다.



### Getter / Setter

생성자 : 객체가 생성될 때 자동 수행되는 메서드이다. return형을 명시하지 않으며, 오버로딩이 가능하다.

Getter / Setter는 Information hiding을 가장 잘 보여주는 메서드이다. private으로  멤버 변수의 접근 제한자를 설정하고, getter / setter를 사용하며 멤버 변수를 호출하거나 수정하는 방식을 사용한다.