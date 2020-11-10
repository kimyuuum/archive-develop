# CPU와 Thread

----

core는 물리적 단위이고, thread는 논리적 단위이다.

**Hyper Threading**

1개의 코어를 가지고 여러개의 코어가 실행되는 것과 같은 수행을 한다. 만약 여러개의 thread의 연산이 독립적이라면, 동시에 수행한다. 하지만 2코어의 성능이 확실히 더 좋다.

</br>

</br>



## Thread

Program의 실행 단위. 하나의 process는 여러개의 thread로 구성 가능하다. 실행 상태가 변경될 때 thread는 context switching을 수행한다. cpu 실행의 기본 단위이다. 한 순간에 하나의 thread만 수행 가능하다.

**process** - OS로부터 자원을 할당받아 독립적으로 cpu에 적재되어 실행되는 작업의 단위. (= 실행중인 program)

**thread** - process 내에서 자원을 이용하여 수행되는 단위.

</br>

**PC Register / Stack**

각각의 thread는 독립적인 작업을 수행해야 한다. stack에서 함수 호출시, 전달 인자, 변수, 되돌아갈 값 등을 관리한다. 그러므로 독립적 함수 호출을 위해 필요한 최소 조건이다.

Thread는 스케줄러에 의해 선점당한다. 명령어가 연속적 수행이 보장되지 않기 때문에 PC Register를 이용해서 기억해야 한다.

</br>

### Thread 동기화 방법의 종류

thread는 여러개가 한 프로세스 안에 존재할 경우 heap과 data 영역의 자원을 공유한다. 그러므로 자원 사용에 대한 동기화가 필요하다.

1. **Mutal Exclusion (Mutex)**

   Thread의 동시 접근을 허용하지 않음을 의미한다. mutex의 thread 동기화 방법은 임계 영역에 들어가기 위해 이 mutex를 가지고 있어야 한다. 임계영역에 들어간 thread는, mutex를 이용해 임계 영역에서 본인이 나올 때 까지 다른 thread의 접근을 막는다. (Lock)

2. **Semaphore**

   mutex와 비슷한 역할이다. 하지만 한개로 한정하지 않고, 접근 순서 동기화에 중점을 둔다. 여러개의 thread가 동시에 접근 가능하다.

3. **Monitor**

   mutex(lock)와 Condition Queue를 가지고 있는 동기화 매커니즘이다.

mutex / monitor는 상호 배제를 통해서 임계 구역에 1개의 thread만 접근 가능하다. semaphore는 1개 이상을 동기화 가능하다.

mutex는 프로세스 단위의 상호 배제를 의미하여 kernel에 의해 제공되고, monitor는 스레드 간의 상호 배제를 의미한다.

</br>

</br>

## Multi Thread

하나의 process를 다수의 실행 단위로 구분지어서 자원을 공유하고, 자원의 생성/관리의 중복성을 최소화해서 수행 능력을 향상시킨다. **하나의 program에서 동시에 여러개의 일을 할 수 있게 한다. multi process는 여러개의 프로그램을 수행하는 것이다.**

### 장점

- process를 이용하여 동시 처리 하던 일을 멀티쓰레드 사용시, 메모리 공간과 자원을 절약 가능하다.
- Thread 간의 통신도 전역 변수 공간 / Heap 영역을 공유하므로, context switching에 대한 오버헤드도 작다.

### 단점

- 동기화 작업이 필요하다.

- A thread가 접근하여 변경중인 자원에 B thread가 접근한다면, 예상 결과와 다를 수 있기 때문이다.

  ⇒ 작업 처리 순서와, 공유 자원의 접근을 컨트롤해야 한다. 하지만 과도한 Lock으로 인해 병목현상이 발생할 수도 있다. 그러므로 동기화가 필요한 공유 자원 부분에서 고려해야 한다.

  병목현상(Bottle neck) : 성능이나 용량이 하나의 구성 요소로 인해 제한 받는 것.

</br>

### CFS ( Completely Fair Scheduler )

**특징**

CFS는 정해진 시간 단위로 봤을 때, 시스템에 존재하는 태스크들에게 공평한 cpu 시간을 할당한다. processor 시간 제공 시, '**balance**'가 가장 중요하다.

**가상 런타임**

balance 결정을 위해 제공된 시간의 양을 관리한다. 프로세스가 액세스 할 수 있도록 허용된 시간이 작은 작업일수록, 더 많은 processor 시간이 필요하다. CFS는 실행 큐가 아니라 RB tree를 이용해서 관리한다. (균형 중요)

</br>

### Multi Processing

두 개 이상의 process(=cpu) 가 협력적으로 작업을 동시에 처리.

하나의 'Task'는 다수의 'Processor'에 의해 처리된다.

여러개의 task가 처리되어야 할 때, 동일한 data를 사용한다면 이 task를 프로세서가 공유하도록 하면 비용이 저렴해진다.또한 하나의 process가 종료된다고 해서 다른 process까지 종료되는것은 아니다.

</br>

### Multi Programming

특정 Process A에 대해서 processor가 작업을 처리할 때 낭비되는 시간 동안 다른 process를 처리한다.  (ex - Interrupt로 인한 block state)

### Multi Tasking

다수의 task를 OS의 스케줄링에 의해 번갈아가며 수행한다. 대표적으로 시분할 System이 존재한다.

**Task** : process보다 확장된 개념. 프로세서가 여러개의 Task를 번갈아가며 처리하기 때문에 동시에 여러 Task가 실행되는 것 처럼 보인다.

차이점 : 멀티태스킹은 그냥 일정하게 주어진 task들을 번갈아가며 처리하는 것이고, 멀티 프로그래밍은 프로세서의 자원이 낭비되는 것을 막기 위하여 블락 상태동안 다른 프로세스를 점유하게 한다.