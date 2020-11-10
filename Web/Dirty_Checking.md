# Dirty Checking

상태 변경 검사

JPA Entity를 조회하면 해당 entity의 조회 상태 그대로 스냅샷을 만든다.

- Transaction이 끝나는 시점에 스냅샷과 비교해서, 다른 점이 존재 할 경우 update query를 DB로 전달한다.

### 상태 변경 검사 대상

→ 영속성 context가 관리하는 entity에만 적용된다.

### 영속성 Context

: entity를 영구 저장하는 환경.

`EntityManager.persist(entity);` → 영속성 context를 통해서 entity를 영속화한다. persist() 시점에는 영속성 context에 저장하고, DB 저장은 이후에 한다.

transaction의 commit 시점에 영속성 컨텍스트에 있는 정보들이 DB에 쿼리로 들어가는것.

1차 캐시가 존재해서 여기서 꺼내쓰기도 한다.