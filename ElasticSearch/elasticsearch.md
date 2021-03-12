# Elastic Search

Status: Doing

Apache lucene기반의 java 오픈소스 분산 검색 엔진. 검색으로 단독 사용하거나, ELK 스택으로 사용한다.

ElasticSearch vs RDB

Database = Index

Table = Type

Column = Field

Row = Document

**Cluster**

가장 큰 시스템 단위를 말한다. 최소 하나 이상의 노드로 이루어진 노드들의 집합. 각각의 클러스터는 data의 접근 / 교환을 할 수 없는 독립적인 system이다.

**Node**

Elasticsearch를 구성하는 하나의 단위 프로세스를 의미한다. 그 역할에 따라 master - eligible, data, ingest, tribe 노드로 구분할 수 있다.

master - eligible node

클러스터를 제어하는 마스터로 선택할 수 있는 노드. master 노드는 인덱스 생성/삭제를 진행하고, 클러스터 노드들을 추적/관리한다. 데이터를 입력할 경우 어느 샤드에 할당할 것인지를 결정한다.

Data node

데이터와 관련된 CRUD 작업과 관련있는 노드.

이 노드는 CPU, 메모리 등 자원을 많이 소비하므로 모니터링이 필요함. master 노드와 분리되는 것이 좋다.

Ingest node

데이터를 변환하는 등 사전 처리 파이프라인을 실행하는 역할.

Coordination only node

data node와 master-eligible node의 일을 대신하는 노드. 대규모 클러스터에서 큰 이점이 존재함. 로드밸런서와 비슷한 역할을 함.

Sharding

데이터를 분산해서 저장하는 방법. 스케일 아웃을 위해 index를 여러 shard로 쪼갠 것을 말한다. 기본적으로 1개가 존재하며, 검색 성능 향상을 위해 클러스터의 샤드 갯수를 조정하는 튜닝을 진행하기도 함.

replica는 shard의 또다른 형태. 노드를 손실했을 경우 데이터의 신뢰성을 위하여 샤드를 복제함. 따라서 replica는 서로 다른 노드에 존재해야함. 

### 특징

Scale out - 샤드를 통해 규모가 수평적으로 늘어날 수 있음.

고가용성 - Replica를 통해 데이터의 안정성을 보장.

Schema Free - Json문서를 통해 데이터를 검색함. 스키마 개념이 없다.

Restful - 데이터 CRUD 작업은 HTTP Restful API를 통해 수행함.

SELECT / GET

INSERT / PUT

UPDATE / POST

DELETE / DELETE

ES가 빠른 이유 = Inverted index(역색인)

 책의 목차 = index, 책 뒤의 키워드로 찾아보기 = inverted index 

ES는 텍스트를 파싱해서 검색어 사전을 만든 다음에, inverted index 방식으로 텍스트를 저장한다.

RDBMS보다 전문검색(full text search)에 빠른 성능을 보인다.

### Real-time 분석

ES는 Hadoop과는 다른 시스템이 사용됨. 하둡 플랫폼 위에서 실행되는 Pig,Hive와 같은 다양한 맵 리듀서들이 제일 많이 사용되는데, ES는 클러스터가 실행되고 있는 동안에는 계속해서 데이터가 입력 ( indexing )  되고, 그와 동시에 실시간에 가까운 속도로 색인된 데이터의 검색 / 집계가 가능하다. ( Near Real Time )

### Full Text 검색 엔진

key - value 형식이 아닌 문서 기반으로 되어 있기 때문에 복합적인 정보를 포함하는 형식의 문서를 있는 그대로 저장이 가능함. 사용자가 직관적으로 이해하고 사용 가능하다.

ElasticSearch에서 질의에 사용되는 쿼리문이나 쿼리에 대한 결과도 모두 JSON 형식으로 전달되고 리턴된다. 그렇기 때문에 CSV,Apache log, syslog와 같은 널리 사용되는 형식들은 logstash에서 변환을 지원하고 있음.

### Multitenancy

서로 다른 인덱스들을 별도의 커넥션 없이 하나의 질의로 묶어서 검색하고, 검색 결과들을 하나의 출력으로 도출할 수 있게 하는 특징

![Elastic%20Search%20b9fdd26e6c6e408386197d557f68b9b4/Untitled.png](Elastic%20Search%20b9fdd26e6c6e408386197d557f68b9b4/Untitled.png)

Leaf Query clauses

특정 field의 value를 보게 한다. match / term / range query가 해당된다.

Compound query clauses

leaf를 wrap해서 사용 가능하다. 로직을 위해 multiple query를 합쳐서 쓰기도 한다. bool이나 dis_max가 해당된다. filter query는 검색 속도를 올리는데에 유용하다. (bool query가 해당됨)

ES Cluster

cluster : 최소 하나 이상의 노드로 구성되어있다.

master node role

인덱스 생성/삭제를 진행하고, 클러스터 노드들을 추적,관리한다. 데이터 입력 시 어느 샤드에 할당할 것인지 확인함.

index = 목차 / inverted index = 키워드.

cluster status : `yellow`  = 모든 data의 읽기/쓰기가 가능하지만 일부 replica shard가 아직 배정되지 않은 상태임.

cluster = node들의 집합

node = shard로 구성

data = shard에 분산되어 저장.

Index (=DBMS)

1개 이상의 primary shard에 매핑되고 replica shard를 가질 수 있음.

Type (=table) , Document (=row)

document를 추가할 경우,  index의 type을 지정해주어야 함.

### Search API

- url 에 파라미터 넘기기 (url search)
- json file에 쿼리 작성해서 POST로 넘기기 (Querydsl)

curl 검색옵션 : `q = QueryStringQuery`

QueryContext = 해당 document가 query절과 얼마나 잘 일치하는가? 관련성 : _score
FilterContect = 해당 document가 query절과 일치하는가? 응답 : true/false, 점수 X

자주사용되는 filter는 성능을 위해 캐싱한다.

Full text Queries

- match

    기본 필드 검색 쿼리. 텍스트/ 숫자/ 날짜를 허용한다.

- bool

    true/false 로직을 사용한다. 

    `must` : 모든 쿼리가 일치하는 document를 조회한다.

    `should` : should절 쿼리 중 하나라도 일치하면 조회한다.

    `must-not` : 모든 쿼리가 일치하지 않으면 조회한다.

    `filter` : score를 무시한다. document가 검색 쿼리와 일치하는지 나타내는 _score값을 계산하지 않도록 쿼리 실행을 최적화한다.

    `range` : 범위에 해당하는 값을 찾는다. (gte - 크거나 같다 / gt - 크다 / lte - 작거나 같다 / lt - 작다)

Term level Queries

 term :  역색인에 명시된 토큰 중 정확한 키워드가 포함된 document를 조회한다.

`string field`

1. text type
2. keyword type =  역색인이 안된다.

term 쿼리 ⇒ ES에서 분석기를 거쳐 역색인이 될 때, lowercase처리를 하기 때문에 'abc'는 검색이 가능해도 'Abc'는 검색할 수 없다.

terms : 배열에 나열된 keyword중 하나라도 존재하면 조회한다.

regexp : 정규 표현식인 termquery를 사용한다.

form / size (pagination)

form = 페이징 수, size = 한번에 나타날 게시글 수.

sort는 특정 필드마다 적용 가능하다.

_source : 명시한 필드들만 response 받을 수 있다

`"_source" : ["firstname","secondname"]`

### Alias

`index의 별명`

alias  변경 ⇒ 삭제 + 추가로 진행해야함.

1. Segment Managing

    데이터를 지울 때 지웠다는 표시만 남겨두고, disk에 남아있다가 백드라운드로 주기적 / 특정 임계치를 넘기면 필요 없어진 data를 정리하고 새로운 segment에 병합한 후 기존 seg를 삭제한다. 

    → disk가 꽉 차면 사용 불가능함.

2. 문서에 TTL 설정

    자동 삭제가 존재하지만 이 방법 또한 segment merging을 사용한다. (deprecated)

Index를 삭제할경우 → 즉시 디스크 삭제를 진행한다.  `_delete_by_query` API보다 효율적임.

Log Rotation

- 일 단위로 새로운 index를 만든다. (Index에 날짜정보 - 현재 존재함)
- 배치 진행한 블럭 데이터는 오늘 생성한 index에 저장한다.
- 가장 오래된 N일 전 생성 Index는 삭제한다.

ES 6.6부터 basic license로 Index LifeCycle Management를 제공한다.  (ILM)

ILM policy

5 phases - hot / warm / cold / frozen / delete

hot phase 

define rollover action. default로 `max_primary_shard_size = 50G` 이거나 `max_age = 30Days` 일 때 rollover 진행한다.

delete phase

set `min_age` to remove index 90 days after rollover.

creation에 대한 time이 아니라 rollover time 기준임.

1. Index template이 필요함. life cycle policy를 설정해주어야 한다. data stream의 definition을 포함해야한다.
2. timeseries도 필요함. `[index.lifecycle.name](http://index.lifecycle.name)` → specify name.
3. index alias로 timeseries를 포함하게 해서 주기적으로 index를 roll over 시키자.