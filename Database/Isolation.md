# Isolation



### Transaction의 격리 수준

동시에 여러 transaction이 처리될 때, 특정 transaction이 다른 transaction에서 변경 , 조회 data 접근 허용 여부를 결정하는 것이다.

</br>

### 격리 수준의 종류

### Read Uncommitted

각 Transaction에서의 변경 내용이 commit이나 rollback 여부에 상관 없이 다른 transaction에서 값을 읽을 수 있다. commit이 되지 않은 상태이지만, update된 값을 다른 transaction에서 읽기가 가능하다.

![image](https://user-images.githubusercontent.com/46887352/98668060-abd51d00-2392-11eb-9896-3bca62405777.png)

문제점

Dirty Read가 발생한다. transaction이 완료되지 않았는데도, 다른 transaction에서 볼 수 있다. 이는 무결성을 해친다.

</br>

</br>

### Read Committed

RDB에서 기본적으로 사용하는 격리 수준이다. 실제 table 값을 가져오는 것이 아니라, undo 영역에 백업된 record에서 값을 가져온다.

![image](https://user-images.githubusercontent.com/46887352/98668069-b099d100-2392-11eb-93eb-e32b4d4ef945.png)

하나의 Transaction에서 같은 query를 호출했는데, 결과 값이 다르다. → repeatable read에 어긋난다.

</br>

</br>

### Repeatable Read

mysql에서는 트랜잭션 마다 transaction ID를 부여한다. 그리고 transaction ID보다 작은 트랜잭션 번호에서 변경한 것만 읽게 한다.

Undo 공간에 백업해두고, 실제 record 값을 변경한다.

백업 data는 불필요하다고 판단하는 시점에 주기적으로 삭제한다. undo backup record가 많아지면, mysql 서버 처리 성능이 저하한다.

![image](https://user-images.githubusercontent.com/46887352/98668086-b68fb200-2392-11eb-80f0-047f8477d2f1.png)

</br>

### Serializable

모든 작업을 하나의 transaction에서 처리하는 것과 같은 높은 고정 수준을 제공한다. 고립 수준이 높아, 동시성 처리 효율은 떨어진다. 한 transaction에서 select 쿼리를 실행하면, 해당 transaction이 commit되기 전까지 다른 transaction에서는 수정,추가,삭제 등의 작업조차 할 수 없다.