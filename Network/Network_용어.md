

## 1. Subnet

​	원래는 하나여야 하는 network를 작은 단위로 분할한다. 이를 표현하기 위한 값이 subnet mask이다.

### Subnet Mask

​	IP 주소의 상위 몇 비트 까지를 network 주소로 사용할지를 정의하기 위해서 사용한다.



## Router

LAN끼리  / LAN - Internet과 같이 서로 다른 network를 상호 연결하기 위해서 사용한다.

IP 주소가 우편 주소라면, router는 우체국이다. 규모가 커지면 router의 직접 송신이 힘들어진다. 그런 경우에는 **적합한 라우터에 전송해서 그 라우터에게 전송을 위임한다.**



## 프록시 서버

내부 network의 컴퓨터를 대신해서 외부 network에 대한 액세스를 해준다. 보통 방화벽에서 작동한다.

**보안상 이점** :  내부 → 외부로 가는 액세스를 집중 관리할 수 있어서 보안상 안전하다.

**유연한 설정 기능** : 사내 인터넷에 액세스 할 수 있는 사용자를 제한하고, 원하지 않는 웹사이트의 열람을 제한 가능하다.



## URL (Uniform Resource Locator)

인터넷에서 파일의 위치를 저장하기 위한 기술이다. 맨 앞 문자열은 파일에 액세스하는 방식이다

`[<http://test.com/test.pdf?docid=111>](<http://test.com/test.pdf?docid=111>)`   ⇒ uri (O)  url (X)

`docid=111` 이것으로 자원을 식별할 수 있으니 identifier.

`~/test.pdf` 까지만 하면 자원의 이름이니 locator

