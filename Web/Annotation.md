# Annotation



@를 이용한 주석.
자바 코드에 주석을 달아 특별한 의미를 부여한 것이다. 프로그램에 관한 데이터를 제공, 코드에 정보를 추가하는 정형화된 방법이다.

### @SpringBootApplication

Spring Boot 자체적으로 기본 설정을 다 한다. 기존에는 Component Scan을 위해 config file 또는 xml 파일이 필요했다면, 이런 파일들이 해당 어노테이션을 사용하여 불필요해졌다.

### @Autowired

construct, field, setter에 사용하여 해당 Bean을 자동 주입시켜주는 어노테이션.

### @ResponseBody

HttpMessageConverter를 이용하여 응답 값을 body에 담는다.

(@RestController는 이미 @Controller 와 @ResponseBody 속성을 포함하고 있기 때문에 필요 없다)

### @RequestBody

요청 Body에 있는 데이터들을 HttpMessageConverter를 이용하여 특정 객체 타입으로 변환시킨다.

@Valid, @Validated를 이용하여 검증 가능하다.