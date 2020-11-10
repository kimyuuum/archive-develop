# Servlet

Java로 Web Application을 개발할 수 있는 스펙과 API를 제공한다. 핵심 Class = `HttpServlet` 

한 요청을 처리할 때 마다 process가 아니라 thread를 만들어서 공유한다.

**servlet container(톰캣)**는 Servlet 스펙에 기반하여, **Servlet의 생명 주기를 다룬다.**



### Log

`[http://localhost:8080/hello](http://localhos:8080/hello)` 를 요청하면

1. Servlet Instance를 만든다.
2. Servlet Instance를 만들고, Get(url로 접근)을 처리하는 doGet()이 실행된다.
3. 이후 주소를 요청하면, Init은 요청되지 않고 바로 doGet()만 호출된다.
4. Tomcat 중지시 Destroy()를 호출한다.