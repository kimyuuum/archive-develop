## Connection Timeout

웹 브라우저가 네이버 서버에 접속하기 위해 서버와 연결된 상태가 되어야 한다. 연결 구성을 위해서는 3-way-handshake가 필요하다.

연결 완료까지 소요된 시간 = connection에 소요된 시간

connection timeout은 connection 구성 요소 임계치이다.

### Socket Timeout

보통 server-client가 established되고 Data를 보낸다. 이때 하나의 패킷이 아니라, 여러개로 나눠서 보내는데, 하나의 패킷에 해당하는 타임아웃 기준이다.

