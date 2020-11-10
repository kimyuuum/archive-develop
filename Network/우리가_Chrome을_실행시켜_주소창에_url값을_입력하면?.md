# 우리가 Chrome을 실행시켜 주소창에 url값을 입력하면?



먼저, 입력한 url이 DNS에 접근한다. 그리고 DNS에서 조회를 진행한다. url을 IP로 바꾸는 과정이다. ARP (Address Resolution protocol)로 대상의 IP에 매칭되는 MAC Address를 알아낸다. 그리고 대상과의 TCP 통신을 통해서 socket을 연다. (3 way handshake를 이용한다)  HTTPS인 경우 SSL / TLS Handshake가 추가된다.

요청한 HTTP Protocol을 서버에서 처리하고, 결과값을 수행한 뒤 다시 client로 처리된 리소스를 웹 브라우저에 표현한 뒤에 보내준다.