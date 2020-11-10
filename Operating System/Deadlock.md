# Deadlock(교착상태)



하나 혹은 두개 이상의 프로세스가 더 이상 계속될 수 없는 특정 사건을 무한정 기다리고 있는 상태.

### 발생 조건

1. Mutal Exclusion

   : 한 프로세스만 CS에 진입할 수 있다.

2. Hold And Wait

   : 이미 어떤 프로세스를 점유하고 있는데 또 다른 프로세스를 점유하기를 원해 기다리는 상황

3. Circular Wait

   : 프로세스와 자원들이 원형을 이루어야 서로가 서로를 기다리는 상황이 발생한다.

4. Non-Preemption

   :  강제 선점이 불가능하다.

   

### 예방 조건

1. Prevention : 애초에 dead lock이 발생하지 않게 설계한다.
2. Avoidance : deadlock 발생 가능성 여부를 검사하고 빠질 가능성이 없을때만 준다.(오버헤드큼)
3. Detect : dead lock 발생 시까지는 계속 수행한다.
4. Recover : dead lock이 발생하는것을 detect 하는 순간 deadlock이 풀릴때까지 계속 process를 종료시킨다.
5. Do Nothing