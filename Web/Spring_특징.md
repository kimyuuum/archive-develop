# Spring의 특징



## IOC와 AOP를 지원하는 경량 Container Framework

## 경량(Light Weight)

Spring은 여러 개의 모듈로 구성되어있다. 각 모듈은, 하나 이상의 jar file로 구성된다. 이러한 jar file 몇개로 개발 실행이 가능하므로 가볍고 빠르다. POJO 형태의 객체를 사용하기 때문에 관리 비용이 적다.

### POJO?

**특정 기술에 종속되지 않은, 순수한 자바 객체. 객체 지향적 원리에 충실하면서, 환경과 기술에 종속되지 않고 필요에 따라 재활용 가능한 방식으로 설계된 Object를 말한다.**

Plain Old Java Object. 말 그대로 옛 자바 객체를 의미한다. Servlet class와 반대 성향을 가진다. servlet class는 우리 마음대로 만들 수 없으며, 반드시 servlet에서 요구하는 규칙에 맞게 만들어야 하지만. POJO는 그렇지 않다. 특정 기술에 얽매이지 않고, 자바의 순수성을 유지하는 객체를 말한다.

</br>

## IOC (Inversion Of Control)

우리가 Business component를 개발할 때에, **낮은 결합도 높은 응집도**에 신경써야한다. Spring은 IOC를 통해서 객체간의 느슨한 결합을 유지한다.

제어의 역전이라는 의미를 가지고 있다. 예전에는 개발자가 객체의 생성 주기를 직접 코드로 관리해야 했던 반면에, Spring을 사용하면, 컨테이너가 자동으로 객체의 생성 주기를 관리한다. **자바 code에 의존 관계가 명시되지 않으므로, 결합도가 낮아져서 유지 보수가 용이하다.**

</br>

## AOP (Aspect Oriented Programming)

관점 지향 프로그래밍. business method를 개발할 때에, 핵심 로직과 각 비즈니스 **메소드마다 가지고 있는 공통 로직을 분리해서 응집도를 올린다.** 공통 기능은 외부의 독립된 class로 분리한다. 

AOP는 애플리케이션 전체에 걸쳐 사용되는 기능을 재사용 하도록 지원한다. 기존 OOP에서는 핵심 비즈니스 로직을 바라보았다면, 관점을 다르게 해서 공통된 요소를 추출하다.

OOP는 객체 지향적 설계, AOP는 절차 지향적 설계이다. OOP에서 핵심 비즈니스 로직의 모듈화가 중심이었다면, AOP는 제 3자 입장에서 기능을 바라보며 공통적으로 쓰이는 기능들을 분리해내는 것 이다.

장점 : Application 전체에 흩어진 공통 기능이 하나의 장소에서 관리된다. 다른 서비스 모듈들이 본인의 목적에만 집중할 수 있다.

### Target

부가 기능을 부여할 대상. 핵심 기능을 담당하는 Service들이다.

### Aspect

부가 기능 모듈. 핵심 기능에 부가되어 의미를 갖는 모듈이다. 부가 기능을 정의한 advice와, 어디에 적용 할지를 결정하는 point cut을 가진다.

**AOP ⇒ 애플리케이션의 핵심 기능에서 부가적인 공통 기능을 분리해서, Aspect라는 모듈로 만들어 설계 / 개발한다.**

### Advice

실질적으로 부가 기능을 담은 구현체. advice의 경우, object에 종속되지 않아 부가 기능에만 집중 가능하다. aspect는 **무엇**을 **언제** 할지를 정의한다.

### Pointcut

부가 기능이 적용될 대상(메소드)를 선점한다. advice를 적용할 join point를 선별하는 기능을 정의한다.

### JoinPoint

advice가 적용될 수 있는 위치. Spring은 method join point만 관리한다.

### Proxy

target을 감싸서, target에 대한 요청을 대신 받아주는 랩핑 오브젝트이다.

client에서 target을 호출하게 되면, proxy가 호출되어 전처리 / 후처리 를 실행한다.

### Weaving

지정 객체에 aspect를 적용해서, 새로운 프록시 객체를 생성한다.

ex) A객체에 aspect가 지정되면, 해당 객체를 위해 proxy를 생성하는 과정.

</br>

## Container

특정 객체의 생성과 관리를 담당한다. 일반적으로 Server 안에 포함되어, 배포 및 구동된다.

Servlet Container = servlet의 생명 주기를 담당한다.

애플리케이션 운용에 필요한 객체를 생성하고, 객체간의 의존 관계를 관리한다. Spring도 일종의 Container라고 볼 수 있다.

</br>

## DispatcherServlet

→ web.xml에 설정해준다.

servlet container에서 HTTP Protocol을 통해 들어오는 모든 요청을 제일 앞에서 처리해주는 프론트 컨트롤러이다. 서버가 받기 전에 공통 처리 작업을 dispatcher servlet이 하고, 적절한 세부 컨트롤러로 작업을 위임한다. 이로 인해 기존 web.xml에 모든 url 매핑 작업을 등록했었는데, 이 역할을 그 전에 dispatcher servlet이 핸들링한다.

## Dependency Injection

의존 주입. 설정 파일을 통해 객체간의 의존 관계를 설정하는 역할이다. 각 클래스 사이에 필요로 하는 의존 관계를, Bean 설정 정보 바탕으로 **컨테이너가 자동 연결**해준다. 객체는 직접 의존하고 있는 객체를 생성하거나 검색할 필요가 없으므로, 코드 관리가 쉬워진다.

</br>

![image](https://user-images.githubusercontent.com/46887352/98669273-834e2280-2394-11eb-871d-69c09d32d619.png)



Spring은 다른 객체들이 사용하고, 다른 service를 위해 사용할 수 있는 class를 컨테이너 형태로 이 기능을 제공해준다. 

A라는 객체에서 B,C 객체를 사용하고자 할 때, A객체에서 직접 생성을 하는 것이 아니라, 외부 (**IOC Container**)에서 생성된 객체를 주입해서 setter / 생성자를 통해 사용한다. 객체를 직접 생성해서 사용하는 경우, 변경하고 싶다면 직접 수정해야 하지만, DI의 특성을 이용해서 설정 file만 변경 해주면 편리해지기 때문에 확장성이나 유지보수에 용이하다.