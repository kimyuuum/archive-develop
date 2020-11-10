# Web Basis



## 용어 정리

- **Ajax (Asynchronous Javascript XML)**

    javascript를 이용한 비동기 통신입니다. client와 server간에 xml을 주고받는 기술입니다. 필요한 부분만 호출해서 사용 가능합니다.

- **Cloud Computing**

    사용자의 환경 밖에서, 서비스로서 제공된 확장 가능한 컴퓨팅 자원을 사용한 양에 따라서, 비용을 지불하고 사용합니다.

- **Saas ( Software As A Service)**

    cloud service의 가장 일반적인 유형입니다. 서비스 제공자가 모든 Infra와 SW 제품을 제공합니다. 

</br>

- **Java Stream**

    Java8에서 새롭게 나타난 기술 중 하나. 

    **Datasource를 추상화**하고, data를 다루는 데 자주 사용되는 메서드를 정의한다.

    ⇒ Datasource가 무엇이든, 같은 방식으로 다룰 수 있음을 의미한다. 코드의 재사용성이 높아진다.

    **특징**

    Stream은 DataSource를 변경하지 않고, 읽기만 합니다. 일회용이기 때문에 컬렉션의 요소를 읽고 나면, 다시 사용 불가인 것 처럼 한번 사용 후 닫힌다.

- **Data Access Object**

    DAO는 직접 DB에 접근하여 관련 데이터들을 가져오는 역할을 한다. mybatis 사용 시, mapper.xml에 쿼리를 작성하고, DAO에 넘겨주는 방식이다.

- **Data Transfer Object**

    각 계층간의 data 교환을 위한 객체이다. Value Object와의 차이점으로는, VO는 read only 특성을 가지고 있다.

- **Thread Pool**

    Application에서 들어온 요청을 작업 큐에 넣고, thread pool은 작업 큐에 들어온 Task 일감을 미리 생성해둔 Thread에 할당한다.

    1. Program 성능 저하 방지 - 매번 발생되는 작업을 병렬로 처리하기 위해 thread를 생성 / 수거하는 데에 비용은 오버헤드가 발생한다. 그래서 미리 Pool 을 만들어두면 효율적이다.
    2. 다수의 사용자 요청 처리 - 다수의 사용자 요청을 수용하고 빠르게 대응 가능하다.
    3. 너무 많이 만들면 메모리 낭비가 발생한다. ex ) 10개 필요한데 100000개 만들었을 경우

- **MySQL**
    - 이미 많은 사용자들이 사용하고 있기 때문에 신뢰도가 높다.
    - 구조가 간단하고, 빠르다.
    - 무료이다.
    - 지원이 잘 되고, 많은 사용자가 쓰기 때문에 구글링을 해도 많은 정보를 얻을 수 있다.
    - 다양한 OS에서 사용 가능하다.

- **Shallow Copy / Deep Copy**

    **Shallow Copy**

    어느 한 객체가 가리키고 있던 참조값만 복사한다. 원본이나 복사본 둘 중 하나를 수정할 경우, 둘 다 동일 객체를 가리키고 있기 때문에 같이 변경된다.

    **Deep Copy**

    원본 참조 변수와, 참조값이 가리키는 객체를 메모리 공간을 새로 할당해서 복사 한다. 원본과 복사본이 개별적인 관계이므로 영향을 서로 끼치지 않는다.

</br>

</br>

## Model - View - Controller

Model - View - Controller 패턴은 코드의 재사용에 유용합니다. 사용자 interface와, 응용 프로그램 개발 소요시간을 줄여줍니다. **Model**은 data와 관련된 핵심 비즈니스 로직을 관리하고, **View**는 사용자에게 보여주는 화면, **Controller**는 model-view 사이의 정보 교환을 연결시킨다.

