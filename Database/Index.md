# Index



## Index

색인. data가 책의 내용이라면, data record address로 index 목록에 있는 sequence number.

DBMS도 DB table의 모든 data를 검색하면 오래 걸리므로, column의 data와 record address를 쌍으로 만들어서 쉽게 접근할 수 있게 한다. 

DBMS의 Index는 항상 정렬된 값을 가지기 때문에, 탐색은 빠르지만 값의 추가 삭제 수정은 실행속도가 느려진다.

Index의 데이터 저장 성능을 희생하고, 대신 데이터의 읽기 속도를 높이는 기능이다.

</br>



### 자료구조

1. B+ Tree Algorithm

    일반적으로 사용되는 인덱스 알고리즘이다.  기본적으로 정렬이 되어있다.

2. Hash Index Algorithm

    컬럼의 값을 해싱해서 Indexing 한다. 검색이 매우 빠르다. 하지만 값을 변형해서 사용하므로, 일부 값만을 이용해서 검색할 땐 사용 불가하다.

### Cluster

여러개의 데이터를 하나로 묶음을 의미한다. Index Cluster는 비슷한 것들을 묶어서 저장하는 형태이다. 주로 비슷한 값들을 동시에 조회하는 경우가 많기 때문이다. 물리적으로 인접하게 저장되어있는 값들이다.

clustered Index = Primary Key값이 비슷한 record를 묶는다.

**Composite Index**

Index로 설정하는 필드의 속성이 중요하다. title, author 순서로 index를 설정하면 title을 search하는 경우, 효과를 볼 수 있다.

### 고려 사항

Index를 생성하면 Insert, Delete, Update 쿼리를 실행할 때 별도의 과정이 필요하다. Insert의 경우, Index에 대한 데이터도 추가해야한다. ⇒ 성능의 손실이 존재한다.

Delete의 경우에도 Index에 존재하는 값은 삭제하지 않고, 사용하지 않는다는 의미의 flag만 설정하므로 row의 수는 그대로이다.

</br>

</br>

### Index와 PK

일반적으로 DBMS에서 PK는 자동으로 인덱스가 적용된다. PK는 개념적인 값이다. 여러 튜플 중, 유일한 튜플임을 보장해준다. 하지만 인덱스는 튜플들의 유일성을 보장하지 않는다. 그냥 DB에서 튜플 결과 값을 빨리 찾기 위해 사용한다. Index는 최대한 중복이 덜 한 값들로 잡아야한다.

primary key는 index적인 특성을 가진다. 그리고 Unique key와 비교해서는 중복이 불가능하고, NULL 허용이 안된다.

</br>

|               |               Primary Key               | Unique Index |
| :-----------: | :-------------------------------------: | :----------: |
|     목적      | Constraint ( Unique + Not NULL) + Index |    Index     |
|    공통점     |               유일성 보장               | 유일성 보장  |
|  참조 무결성  |        PK / FK에 의해 지정 가능         | 지정 불가능  |
| 태이블당 개수 |                   1개                   | 여러개 가능  |
|     NULL      |                 허용 X                  |     허용     |

</br>

**Unique Index의 장단점**

장점 

+ PK / FK가 없어 Database 변경에 유동적이다. (관리가 쉬움) 개발 시점에 data의 제약이 없다.

단점 

+ 무결성이 깨질 수 있다. → 데이터 정리 작업이 필요하다.

+ PK가 무엇인지 구분 불가능하다.

</br>

**Primary Key의 장점**

DB에 대해 PK / FK 설정이 가능하다. 

→ **참조 무결성** 제약 조건 지정이 가능하고, 무결성 오류 방지가 가능하다.