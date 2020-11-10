# Spring 구동 방식



![image](https://user-images.githubusercontent.com/46887352/98669812-269f3780-2395-11eb-85fe-85270a68a9de.png)

1. client가 url을 요청하여 요구사항에 맞는 특정 HTTP Method를 전송합니다.
2. Dispatcher Servlet이 해당 요구사항에 맞는 요청을 처리하는 Controller가 있는지 먼저 처리를 합니다.
3. 해당 요구사항에 맞는 Controller와 Mapping을 진행합니다.
4. Controller가 비즈니스 로직을 실행하고, 다시 실행 결과를 Dispatcher Servlet에게 넘깁니다.
5. 결과를 브라우저에 출력하기 위한 View를 찾기 위해, View Resolver를 통해서 맞는 view를 검색합니다.
6. view에서 브라우저에 출력하기 위한 html / css 작업 등이 이루어집니다.
7. Dispatcher Servlet을 통해서 브라우저에 필요한 결과 값과 화면 등이 다시 client에게 response됩니다.