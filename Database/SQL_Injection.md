# SQL Injection

악의적인 사용자가 보안상의 취약점을 이용해서, 임의의 SQL문을 주입하고 실행되게 하여 DB가 비정상적인 동작을 하도록 조작하는 행위.



```sql
SELECT * FROM USERS WHERE id= 'INPUT1' AND password = 'INPUT2';

INPUT1 = "OR 1=1 --" 
//where절의 쿼리를 모두 참으로 만들고, --를 넣어 뒤를 주석으로 만든다.
```



### 해결 방안

- 입력 값에 대한 검증

    select,drop,update,@,... 등 입력값이 sql문에 영향을 끼치는 구문들을 공백이 아닌 다른 문자로 바꾸어야 한다.

- 권한을 엄격하게 가져야 한다.
- 기본 DB error message에 table,column이 노출될 수 있으므로, 유의해야 한다.
- 신뢰 가능한 network에서만 접근하게 한다.