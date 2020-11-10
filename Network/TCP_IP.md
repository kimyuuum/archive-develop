

# TCP/IP



전송 제어 프로토콜. IP 계층은 데이터를 상대 HW에 전송하고, TCP는 패킷을 추적 / 관리한다.



## Application

응용 프로그램들이 network service, mail, web service를 할 수 있도록 표준 Interface를 제공하는 계층이다.

ex) HTTP, DNS, SMTP ...



## Transport

Network endpoint에서 신뢰성 있는 전송 기능을 제공한다. TCP / UDP 등의 프로토콜이 존재한다. 통신 노드간의 연결을 제어하고, 자료 송수신을 담당한다.



## Internet

Transport 계층으로부터 받은 data에 ip 패킷 헤더를 붙여서 ip 패킷을 만들고, 이를 전송한다. Addressing, Packaging, Routing을 제공하는 계층이다.

핵심 Protocol - I**P (Internet Protocol)**

IP Addressing과 패킷의 분해 / 재조합을 한다. ARP를 이용한다. (Address Resolution Protocol)을 이용해서 IP 계층 주소를 MAC address로 변환해서 network 계층에 전송한다.



## Network Address

HW와 관련된 모든것을 지원한다. **MAC주소**가 사용되는 계층이다. TCP/IP 패킷을 네트워크 계층으로 전달하고, 받아온다. 에러 검출 / 패킷의 프레임화를 담당한다.

MAC 주소를 이용해서 패킷을 전송할 곳을 판단한다. 스위치, 허브 등이 해당 계층에서 사용된다.



## Packet?

인터넷 내에서 데이터를 효율적으로 전송하기 위해 데이터를 일정 크기로 쪼개어 분할하여 전송하는 방식이다. **routing을 효율적**으로 하기 위해 고안된 방식이다.

### Virtual Circuit

TCP에서 사용하는 방식. packet이 지나간 경로에 가상의 회선을 배치한다. 첫 통신 연결이 이루어질때 미리 한 경로를 효율적으로 계산해놓고, 계속해서 그 경로만을 사용한다. 그래서 패킷이 순차적으로 전송되고, 수신자도 순차적으로 패킷을 받을 수 있다. 경로가 고장나면 패킷을 더이상 전송할 수 없다.

### Datagram

상대방의 수신 여부는 판단하지 않는다. 각각의 패킷이 독립적으로 전송되기 때문에 경로가 모두 다 다르다. 한 라우터가 고장났을 경우에는 패킷이 그 경로를 사용하지 않고 개별적으로 우회하여 전송이 가능하다. UDP가 사용하는 패킷 전달 방식으로, 신뢰성은 Virtual Circuit보다 떨어지지만 속도가 빠르기 때문에 Streaming Service에서 사용되는 방식이다.

각각의 router가 network 속도를 기준으로 경로를 판단하여서 목적지를 찾아간다. packet을 받을 때마다 경로를 생각해야한다.