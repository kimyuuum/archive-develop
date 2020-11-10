# Race Condition



multi thread / process program에서 어떤 shared data를 접근하는 경우에 순서를 조절한다. → Synchronization



## Race condition

두 개 이상의 concurrent한 thread들이 공유된 자원에 접근하려고 할 때, 동기화 매커니즘 없이 접근하려고 하는 상황.

→ 두 개의 thread가 하나의 자원을 놓고, 서로 사용하려고 경쟁하는 상황이다. 이러한 문제점을 디버깅 타이밍에 찾기가 힘들다.

multiThread Programming시 중요하다.



![image](https://user-images.githubusercontent.com/46887352/98632592-24bc8080-2363-11eb-8a37-e523b447e0f9.png)



### 해결 방안

1. Mutal Exclusion

   Semaphore - 각 프로세스에 제어 신호를 전달해서, 순서대로 작업을 수행하도록 하는 기법. resource의 상태를 나타내는 counter이다. 해당 값에 따라 OS는 proc가 즉시 자원을 사용할 지, 자원이 다른 proc에 의해 사용중일 경우 일정 시간 기다려야 한다.

   Mutex - 0 또는 1의 값을 가지는 이진 semaphore와 방법이 유사하다. CS를 가진 thread들의 실행 시간을 서로 겹치지 않게 단독 실행 가능하다. locking / unlocking을 사용한다.

   Semaphore는 소유가 불가능하다. Mutex는 소유하고 있는 thread가 mutex 해제도 가능하다.

   