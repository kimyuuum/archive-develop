# OAuth



## OAUTH?

인증을 위한 오픈 standard protocol이다.

사용자가 Internet Service의 기능을 다른 애플리케이션에서도 사용할 수 있게 한다. Oauth 2.0 은 1.0보다 인증 절차가 간단하다.



### Oauth Login

회사원이 사원증을 이용해서 출입을 하는 것은 **Login**

외부 방문자가 출입증을 받아 출입하는 것은 **Oauth**

Auth는 Authentication(권한) , Authorization → OAUTH의 주요 목적 ( 허가 ) 둘 다 포함하고 있다.

OpenID = 인증을 위한 표준 프로토콜. HTTP를 사용한다는 점은 OAUTH와 같다.

근본 목적 → 해당 사용자의 wall에 글을 쓸 수 있는 API 호출 권한이나, 친구 목록을 가져오는 API를 호출할 권한이 있는 사용자인지 확인한다.

### Oauth Dance

Oauth를 이용하여 사용자를 인증하는 과정이다.

- consumer가 service Provider로부터 client key와 secret를 발급 받아야 한다.
- 그리고 Request Token을 요청할 때, consumer 정보를 포함하여 발급받는다.
- request token 값을 발급 받으면, consumer는 user 를 service provider의 인증 사이트로 리다이렉트 시키고 유저는 그곳에서 service provider user임을 인증한다.
- 그러면 consumer는 인증을 확인하고 oauth token과 oauth verifier를 넘겨준다.
- 그 이후에 access token을 요청하고, 토큰과 서명들이 인증이 되었으면 service provider는 access token을 넘겨준다.
- 그리고 access token을 이용하여 service Provider 정보에 접근한다.



</br>

</br>

## Oauth2.0

OAuth 1.0은, 웹 애플리케이션이 아닌 환경에서는 사용하기 까다롭고, 절차가 복잡합니다.

그래서 2.0이 등장하게 되었는데요, SSL을 사용하여 인증 과정을 간소화 한 것으로 알고 있습니다.

또한 보안을 위해 Access Token에 Lifetime을 지정합니다.

### Authorization Code Grant

웹 앱이나, native 앱에서 access token을 얻는데에 사용되는 인증입니다.

- client가 redirect url을 포함하여서 authorization server 인증 요청을 합니다.
- Authorization server는 유저에게 로그인 창을 제공해서 인증합니다.
- Authorization server는 Authorization code를 client에게 제공합니다.
- client는 code로 authorization server에 access token을 요청합니다.
- authorization server는 client에게 access token을 발급합니다.
- 이후 access token을 이용해서 client는 authorization server resource를 접근합니다. 그 이후에 토큰이 만료된다면, refresh token을 이용하여 재발급이 가능합니다.