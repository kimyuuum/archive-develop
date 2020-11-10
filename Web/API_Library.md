# API / Library

[API vs Library (What's the Difference?)](https://rapidapi.com/blog/api-vs-library/)

### API  (Application Programming Interface)

응용 프로그램에서 사용할 수 있게 OS나 programming 언어가 제공하는 기능을 제어할 수 있게 만든 Interface. 

![image](https://user-images.githubusercontent.com/46887352/98670325-e7bdb180-2395-11eb-913c-781e8c3aace9.png)

</br>

### Library

사전에 만들어진 코드의 집합. `재사용`이 가장 중요한 목적이다.

개발자들이 Application을 제작할 때, 특정한 기능은 변하지 않을 수 있다. 그러므로 해당 코드를 계속 반복해서 사용하는 것 보다, 개발 생산성 향상을 위해 library를 사용한다.

</br>

### 차이점

실행중인 code가 다른 실행중인 code와의 소통을 원한다면 API가 필요하다. 라이브러리는 코드 그 자체를 제공해주고, API는 Interface를 제공한다. API의 특정 기능이 제작되기 위해서, 몇몇의 라이브러리로 구성될 수 있다. 그러나 library 그 자체는 api가 아니다. 쓰기 편한 기술이나 기능의 집합에 더 가깝다. 

![image](https://user-images.githubusercontent.com/46887352/98670333-eab8a200-2395-11eb-8e94-c521635258b9.png)

</br>

### Framework

Application 개발을 위한 코드,알고리즘,DB연동 등 기능을 위해 어느정도 뼈대를 제공해준다.

→ 이 위에 코드를 작성해서, Application을 완성시킨다.

### 차이점 - Inversion Of Control

`Flow에 대한 권한이 어디에 있는가?`

framework는 자체적으로 흐름을 가지고 있다. 개발자는 그 흐름 안에서 코드를 작성하고, Library는 개발자가 직접 흐름에 맞게 제어하며 적재 적소에 가져다 써야 한다.

