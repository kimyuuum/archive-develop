# Java Reflection

JVM에서 실행되는 애플리케이션의 runtime 동작을 검사하거나, 수정할 수 있는 기능이 필요한 program에서 사용한다.

class 구조를 개발자가 확인 가능하고, 값을 가져오거나 메서드를 호출할 때 사용된다.

ex) Spring Framework, hibernate

Spring Framework - runtime시에 개발자가 등록한 Bean을 애플리케이션에서 가져와서 사용 가능하다.

### 특징

확장성 - 애플리케이션은 정규화된 이름을 사용하여 확장성 객체의 인스턴스를 생성하고, 외부 사용자가 정의한 class를 사용 가능하다.

**캡슐화를 저해한다.**  private한 property 및 method에 액세스 하는 것과 같이, 비 reflection code에서는 작동하지 않는 것도 수행한다.