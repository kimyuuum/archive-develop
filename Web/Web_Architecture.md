# Web Architecture

![image](https://user-images.githubusercontent.com/46887352/98669131-4aae4900-2394-11eb-910d-4f8a247997c8.png)

### DNS

Domain Name Server. domain 에서 IP 주소로의 key / value 조회를 제공한다.



### Load Balancer

Application의 수직 / 수평적 확장이 존재한다.

수직적 확장 : 이미 사용중인 장치의 성능을 올린다.

수평적 확장 : 더 많은 장치를 새로 추가한다. 서비스 중단을 막기 위해선, 수평적 확장이 중요하다.

1대 이상의 서버를 가지며, 이를 예방하자

→ Load balancer를 이용해서, request를 많은 application 서버중 하나로 연결하고, response를 client로 전송한다.



### Web Application Server

사용자의 request가 들어오면, 핵심 비즈니스 로직을 실행하고, 결과를 HTML에 담아 브라우저로 전송한다.

DB, Job Queue, 캐싱 등 다양한 인프라와 통신해야 한다.



### DB

Data 구조를 정의하고, CRUD를 실행한다.



### 캐싱 서비스

정보를 O(1)안에 찾을 수 있는 key / value 저장소를 제공한다. 자원이 많이 소모되는 연산의 결과를 다시 계산하지 않고, 캐시에서 가져온다.