# 다이아몬드 문제



다중 상속을 지원하는 경우 발생할 수 있는 문제이다.

![image](https://user-images.githubusercontent.com/46887352/98635039-a2828b00-2367-11eb-9d37-206e49252c1a.png)

**Son이 Father A / B 둘 중 어느 myMethod()을 상속받아야 할 지에 대한 충돌이 생긴다. 애초에 이런 충돌을 방지하고자 Java는 다중 상속을 지원하지 않는다.**

Java Interface는, 기능에 대한 선언만 하면 되기 때문에 다이아몬드 상속이 되더라도, 충돌의 여지가 없다.

Interface의 경우 내용이 겹쳐도 결국 최종 구현 부분은 구현 객체에서 이루어지기 때문이다.