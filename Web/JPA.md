# JPA

## Java Persistent API / Object Relational Mapping

JPA는 ORM 기술에 대한 API 표준 명세이다. ORM을 사용하기 위한 인터페이스를 모아두었고, Hibernate가 대표적입니다.

### ORM

객체와 DB의 table이 매핑을 이루는것을 말한다. 객체가 table이 되도록 매핑시켜주는것. 생산성이 높아져 코드에 집중 가능하다. raw query보다 속도가 느리긴 하다.

### Querydsl

Domain Specific Language.

SQL을 java로 type safe하게 작성할 수 있게 해주는 framework이다. Spring Data JPA에서는, Custom Repository를 이용하여 JPARepository를 상속받는 형태를 가집니다.



![image](https://user-images.githubusercontent.com/46887352/98670148-97deea80-2395-11eb-8ca0-537a00362803.png)



### Dirty Checking

상태 변경 검사. 상태의 변화가 생겼을 때에, JPA의 transaction이 끝나는 시점에 변화가 있는 모든 entity 객체를 db에 자동 반영합니다.

@DynamicUpdate를 사용하여, 전체 필드 변경 업데이트 쿼리에서, 변경 필드만 업데이트가 되게끔 했습니다.