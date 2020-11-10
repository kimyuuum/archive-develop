# Caching

## Web Server 기준



![image](https://user-images.githubusercontent.com/46887352/98670235-be048a80-2395-11eb-8ae6-c636ba651d63.png)

- 웹 서버로 요청시, 하드 디스크가 캐시를 확인한다.

**Cache miss** 발생 → 다시 요청받은 경우가 있다면, 캐시를 하드 디스크에 저장한다.

→ 이후 캐시를 사용 가능할 경우, **Cache Hit**가 발생한다. Cache Miss 발생 전까지, Buffer에서 Cache가 제공.

</br>

### Response Caching

웹 서버는, 응답을 캐싱하도록 구성해서 유사 요청이 호스트로 전달되지 않게 할 수 있다.

웹 서버의 response는 메모리에 캐싱한다.

### Memoization

캐싱의 한 형태.

컴퓨터 program이 동일한 계산을 반복해야 할 경우, 이전 계산값을 메모리에 저장한다. 이렇게 동일 계산의 반복 수행을 제거하여 program의 실행 속도를 빠르게 한다.

함수의 입력 parameter / 결과값을 매칭한 조회 테이블을 통해 구현된다.

</br>

### Http Header를 통한 브라우저 캐싱

- 모든 Browser는 resource 임시 저장을 위해 HTTP 캐시 (웹 캐시) 구현을 제공한다.
- resource가 로컬 캐시로부터 빠르게 로드되기 때문에, 속도가 빠르다.
- 요청이 network를 통하지 않아서, 왕복 시간 (Round Trip Time)이 발생하지 않는다.

</br>

## Database Cache

: DB 쿼리는 DB 서버에서 수행되기 때문에 사용자가 급격히 증가함에 따라 속도가 매우 느리거나 부하가 몰릴 수 있다. 반복되는 쿼리를 DB에 캐싱해서 응답 시간을 줄이자.