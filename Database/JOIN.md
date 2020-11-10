# JOIN



## JOIN

연관된 튜플들을 결합하여 새로운 relation을 return한다. Join 조건에 만족하지 않는 튜플도 결과로 출력하기 위한 방법이다.



### Inner Join

**Equi Join** - 연결고리가 되는 공통 속성을 join 속성이라고 한다. 공통 속성을 기준으로 '=' 비교에 의해 같은 값을 가지는 행을 연결하여 결과를 생성한다.

table join을 하는 경우, 한 테이블에만 있는 속성은 테이블 이름을 생략 가능하지만, 두 테이블에 모두 속해있는 속성은 속성 이름을 table name과 함께 표현한다.

join 조건이 '=' 일 때, 동일 속성이 2번 나타난다.  

중복된 속성을 제거하여 1번만 표기하는 법 : Natural Join.

**Non Equi Join** - '='조건이 아닌 나머지 비교 연산자를 사용하는 join.

### Outer Join

join 조건에 만족하지 않는 tuple도 결과로 출력해준다.

**Left/Right Outer Join**   - Inner Join의 결과를 구한 후, 우측/좌측 relation에 어떤 tuple과도 맞지 않는 좌측 / 우측 relation에 있는 tuple에 null을 붙여 Inner Join 결과에 추가한다.