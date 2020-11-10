# @Bean



Spring IOC Container가 관리하는 java 객체.

new 연산자로 생성 → Bean (X)

ApplicationContext.getBean() → Bean (O)

- ApplicationContext가 알고 있는 객체, 만들어서 그 안에 담고 있는 객체를 의미한다.

</br>

### Bean 등록 방법

1. @ComponentScan

    `@ComponentScan` , `@Component` 를 사용해서 bean을 등록한다.

    → 어느 지점부터 component를 찾으라고 알려준다.

    → 실제로 찾아서 bean으로 등록할 클래스를 명시한다.

    `@SpringBootApplication` 은 내부적으로 `@ComponentScan`을 사용한다.

    `@Controller`는 `@Component`를 사용한다.

2. Bean 직접 등록하기

    java class를 직접 생성해서, ~Configuration으로 명명한다.

    class 상단에 `@Configuration`을 붙여주고, `@Bean`을 이용해서 직접 bean을 정의한다.

    configuration annotation은 component annotation을 사용하므로, component scan의 scan 대상이 된다.