# JDBC Driver

- Application 내의 오류가 명확히 확인되지 않았는데, out of memory 발생.
- DB 서버에서부터 발생한 장애로 일어난 Server error
- DB에서 원하는 데이터를 가져오는 과정에서, 물리 DB 서버에 최초 연결되어 connection 객체를 생성할 때 비용이 가장 크다.

![image](https://user-images.githubusercontent.com/46887352/98635386-3b190b00-2368-11eb-9f14-eef58666281a.png)

Web Application은 HTTP 요청에 따라 Thread를 생성한다. 대부분 DB로부터 Data를 얻는다.

만약 모든 HTTP Connection에 대해서 Driver를 load하면, connection 객체를 생성, 연결 할 때에 큰 오버헤드가 발생한다. ⇒ 물리 DB에 지속 접근이 필요하다.

이 수행을 줄이기 위해 DB Connection Pool을 사용해서 일정 시간을 두고, connection 객체를 유지시킨다. Thread를 효율적으로 처리 가능하다.

### Connection Pool 구현체 역할

1. WAS가 실행되면서 미리 일정량의 DB Connection 객체를 생성하고 pool에 저장한다.
2. HTTP Request에 따라 필요할 때 Pool에서 connection객체를 사용하고 다시 return해준다.

⇒ Pool Connection을 Idle(대기) 상태로 두고, 실제 사용(active)한다.