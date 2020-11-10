# Dialect



JPA는 Application이 직접 JDBC level에서 sql을 작성하는 것이 아니라, JPA가 직접 SQL을 작성하고 실행하는 형태이다.

⇒ JPA를 이용하면 쿼리를 작성할 필요도 없고, DBMS별로 조금씩 다른 SQL 방언 걱정을 하지 않아도 된다. JPA에서는 Dialect라는 추상화된 방언 class를 제공하고, 각 벤더에 맞는 구현체를 제공한다.



![image](https://user-images.githubusercontent.com/46887352/98662747-96102980-238b-11eb-867e-6e9c8af3d4bb.png)



해당 Dialect만 잘 설정해주면, 알아서 쿼리를 생성한다.