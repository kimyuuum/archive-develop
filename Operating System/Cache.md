# Cache



Processor가 아무리 빨라도, 메모리가 느리면 효율이 떨어진다. 이를 개선하기 위해 캐시를 사용한다.

- 캐시에 자주 사용하는 Data를 담아두고, 필요시 processor가 메인 메모리 대신 캐시로 접근해서 처리 속도를 높인다.

</br>

### Principle of Locality

`자주 사용하는 것`에 대한 판단 기준은 **시간 지역성**과 **공간 지역성**이 존재한다.

- 시간 지역성 : 최근 접근한 data에 다시 접근한다.
- 공간 지역성 : 최근 접근한 data의 주변 공간에 다시 접근한다.

</br>

### Cache의 종류

1. L1 Cache
   - Instruction cache : 메모리의 text 영역을 다룬다.
   - data cache : text 영역을 제외한 모든 data를 다룬다.
2. L2 Cache : 용량이 큰 캐시
3. L3 Cache : 멀티 코어 System에서 여러 코어가 공유하는 캐시.

**Hit** - cpu에서 요청한 data가 캐시에 존재하는 경우.

**Hit Latency -** hit가 발생해 캐싱된 data를 가져올 때 소요되는 시간.

**Miss** - cpu에서 요청한 data가 캐시에 존재하지 않는 경우.

**Miss Latency** - miss가 발생해 상위 캐시에서 data를 가져오거나, 메모리에서 데이터를 가져올 때 소요되는 시간.

### 캐시 성능 올리기

1. 캐시 크기를 줄여, Hit Latency를 내린다.
2. 캐시 크기를 늘려 miss rate를 감소시킨다.
3. 더 빠른 캐시로 latency를 줄인다.

### Cache organization

- 주소가 key로 주어지면, 해당 공간에 즉시 접근이 가능하다.

⇒ 캐시가 **하드웨어로 구현한 hashtable과 같다.**

캐시가 빠른 이유는, hash table의 검색 Time Complexity가 O(1)이기 때문이다.