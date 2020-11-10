# Thread Safe

> MultiThread 환경에서 일반적으로 어떤 함수나 변수, 객체가 여러 thread로부터 동시에 접근이 이루어져도, 프로그램의 실행에 문제가 없음을 말한다.



### 1. Re-enterancy

어떤 함수가 한 thread에 의해 호출되어 실행중일때, 다른 thread가 그 함수를 호출하더라도, 결과가 각각 올바르게 이뤄져야함. 

### 2. Thread - local Storage

공유 자원의 사용을 최대한 줄여서 각 thread에서만 접근 가능한 저장소들을 사용하며 동시 접근을 막는다. 공유 상태를 피할 수 없을 때 사용한다.

### 3. Mutal Exclusion

제일 많이 이용되는 방식. 한 Thread가 자원을 사용중이라면, Semaphore등을 이용하여 Lock 상태로 진입하여 작업을 실행하고, 작업이 끝날 때 까지 Lock을 해제하지 않으며 다른 Thread로부터 접근을 막는다.

### 4. Atomic Operations

공유 자원에 접근할 때, 원자 연산을 이용하거나 원자적으로 정의된 접근 방법을 사용하며 상호 배제를 구현한다



