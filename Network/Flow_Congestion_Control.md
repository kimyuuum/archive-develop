# Flow / Congestion Control



## Flow Control

수신측 buffer가 overflow 되지 않도록 송신 측이 전송 속도를 조절한다. Internet에서 데이터 전송 지연의 변동이 심하다. 따라서 손실된 데이터를 재전송하는 timeout 설정이 중요 issue이다.

⇒ Sliding Window를 사용하자.

### Sliding Window

Flow Control(Window 크기를 조절하며 수행) 과 ACK역할(그냥 data 전달 여부 확인)을 분리한다.

전송, 수신 스테이션 양측에서 만들어진 버퍼의 크기이다.

## Congestion Control

송신(host) 과 Router(network) 둘 사이의 data 전송 속도 처리를 위해서 라우터가 처리할 수 있는 양을 넘으면 데이터 손실 우려가 있다. 이를 위해 제어한다.

**Slow Start** : 패킷이 문제 없이 도착하면 각 ACK 패킷마다 Window Size를 1씩 늘린다. 한 주기가 지나면 Window Size가 2배가 된다. 만약 혼잡이 발생 할 경우 1씩 감소시킨다.

## ARQ (Automatic Repeat Request)

frame이 손상 되었거나 손실되었을 경우, 재전송을 통해 오류를 복구한다. 신뢰성 있는 Data전달을 위해 재전송을 기반으로 한 에러 제어 방식이다.

### Stop - Wait ARQ

전송측은 수신측에서 보내준 ACK를 받을때까지 프레임의 복사본을 유지한다. 식별을 위해 Data Frame과 ACK 프레임을 각 0,1을 부여한다.

수신 측이 Data를 받지 못했을 경우, NAK를 보내고 이를 받은 송신측은 재전송한다. 만약 ACK나 data가 분실되었을 경우, 일정 간격 시간을 두고 time out이 되면 재전송한다.

### Go Back N ARQ

전송된 frame이 손상되거나 분실될경우, 확인된 마지막 frame 이후로 모두 재전송한다. sliding window는 연속적인 frame 전송 기법으로, 전송 측은 ACK를 받기 전까지 data를 모두 가지고 있어야 한다. ACK와 NAK도 구별을 할 수 있어야 한다.

ACK 수신 → 다음 Frame을 전송한다.

NAK 수신 → 해당 Frame 자체 번호를 return한다.

재전송 되는 경우

1. NAK Frame을 받은 경우

   go back n ARQ의 특징은 데이터를 재전송하는 부분이다. n을 재전송 하는 경우, n 이후의 데이터들을 모두 재전송해야한다.

2. 전송 Data Frame이 분실된 경우

   확인된 data 이후의 모든 데이터 재전송과 수신측의 폐기이다. 수신측에서 1을 받았는데 3을 받았을 경우?

   → 수신측은 3을 폐기하고 NAK2를 보낸다. 그럼 송신측은 2부터 재전송을 실시한다.

3. ACK가 분실된 경우

   전송측은 lost ACK를 위해 Timer가 존재한다. timer의 타임아웃때까지 못받을 경우, 마지막 ACK부터 재전송한다.

### Selective - Reject ARQ

Go Back N ARQ의 단점을 보완한 방법이다. NAK를 받은 해당 데이터만 재전송하면 된다. 그럼 수신측에서는 해당 데이터를 받았을 경우 재배열을 통하여 데이터를 정렬한다. 이를 위해 별도의 버퍼도 필요하다.