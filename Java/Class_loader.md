# Class Loader



로딩 → 링크 → 초기화 순서.

### Loading(로딩)

클래스 로더가 .class 파일을 읽고, 내용에 따라 적절한 바이너리 데이터를 만들어 Method 영역에 저장한다.

1. Type 정보 ( 클래스, Interface, Enum)
2. 메소드와 변수

로딩이 끝나면 해당 classType의 class 객체를 생성하여 힙 영역에 저장한다.

→ 못 찾으면 classNotFoundException;

### Linking(링크)

Verify → Prepare → Resolve

1. .class file 유효성을 체크한다.
2. 클래스 변수(static)와 기본값에 필요한 메모리를 준비한다.

### Initialization

링크에서 prepare 단계에서 확보한 메모리 영역에 static을 할당한다.