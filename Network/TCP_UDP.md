## TCP? (Transmission Control Protocol)



신뢰성과 순차적인 진행을 수행합니다. 송/수신자가 소켓이라고 부르는 endpoint를 생성함으로써 이루어집니다.

- 전이중 Point to Point 방식이다.

  full - duplex : 양방향 연결을 뜻한다.

  Point to Point : 정확히 2개의 endpoint를 가진다.

- 1:1연결만을 지원하기 때문에 multicast나 broadcasting을 지원하지 않는다.

</br>

## Feature

1. **Connection Oriented**

   2개의 endpoint 사이에 연결을 먼저 맺고, data를 주고받는다.

2. **Bidirectional byte stream**

   양방향 데이터 통신을 하고, byte stream을 사용한다.

3. **Inorder Delivery**

   순차적으로 전송된 순서대로 수신자가 수신한다.

4. **Reliability through ACK**

   ACK를 받아야만 완전히 수신됐다고 생각한다. ACK를 받지 못하면 해당 데이터에 대해서 재전송을 실시한다.

5. **Flow Control / Congestion Control**

   흐름 제어/혼잡 제어가 가능하다.

</br>

### 3-way-handshake (connection)

![image](https://user-images.githubusercontent.com/46887352/98633969-d3fa5700-2365-11eb-82cd-1bfc351d5a0d.png)

client가 server에 연결하고자 SYN을 보내면, server는 wait상태에 있다가 연결 요청을 받고 요청을 수락한다는 ACK와 함께 SYN 데이터를 보냅니다. client는 서버의 요청 수락 대기 상태에 있다가 ACK를 받고, 서버가 보낸 SYN에 대한 ACK를 다시 한번 보냅니다. 이렇게 서로가 통신이 잘 됨을 확인하면 그때부터 연결이 성립됩니다.

</br>

### 4-way-handshake (Termination)

![image](https://user-images.githubusercontent.com/46887352/98633977-d957a180-2365-11eb-982b-d5f3084ee081.png)

연결이 되어있던 상태에서 client가 server에게 연결 종료 요청을 위해 FIN 메시지를 보냅니다. 그럼 server는 fin에 대한 ack를 전송하고, 서버를 종료합니다. 종료하기 전 까지 모두 데이터를 보낸 뒤에, 서버가 완전히 끝났다는 신호인 FIN을 한번 더 보냅니다. 그럼 client는 그때 Server의 FIN flag에 대한 ACK를 마지막으로 보내고, 완전히 closed됩니다. client는 이때 혹시 server에서 전송되는 잉여 데이터를 받기 위해 바로 종료하지 않고, 일정시간 time_wait 상태로 있다가 종료합니다.

</br>

**SYN** : Synchronize Sequence Number

**ACK** : Acknowledgement

</br>

### Handshake가 필요한 이유

TCP는 신뢰성을 기반으로 하는 양방향 연결이기 때문에 서로간의 통신이 잘 되는지 확인을 해야 합니다. 그러므로 client → server, server→ client 간의 연결이 잘 되는것을 확인하고 마지막으로 client가 server의 통신을 잘 받았다는 것 또한 확인해줘야 합니다.





# UDP (User Datagram Protocol)



Data Packet을 Datagram 단위로 처리한다.

1. 비연결형 서비스. datagram 방식을 제공한다.
2. 정보를 주고 받을 때에 신호절차가 없다.
3. 헤더의 checksum으로만 에러를 검출하기 때문에, 간단한 방식을 사용한다.
4. 신뢰성이 낮다 → streaming과 같은 연속성 위주의 처리를 한다.

</br>