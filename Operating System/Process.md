# Process

-------



**실행중인 Program**. 디스크로부터 메모리에 적재되어 CPU의 할당을 받을 수 있는것이다. OS로부터 주소 공간, 메모리 등 자원을 할당받고, 이것을 Process라고 한다.

</br>

### 생성 과정

1. PCB가 생성되어 OS가 프로그램의 코드를 읽고 process에 할당된 메모리의 text / data segment에 내용을 적재한다.
2. Heap / Stack은 초기 메모리 주소만 초기화 한다.
3. PCB에 정보가 기록되면 Ready Queue에 진입해서 실행되기를 기다린다.

</br>

### Process의 주소 공간

각 프로그램마다 별도로 주소 공간을 가진다. 이를 가상 메모리 (논리 메모리)라고 한다.

![image](https://user-images.githubusercontent.com/46887352/98631949-d195fe00-2361-11eb-9f10-354f9c421570.png)

</br>

</br>

**Code Segment & Data Segment**

실행 파일이 가지고 있던 코드는 Code 영역에, 그 코드 안에 담긴 전역 변수와 같은 정적 할당이 필요한 요소들이 Data 영역에 저장된다.

**Heap & Stack**

Heap에는 파일이 실행되며 동적 할당이 필요할때 생성 / 해제되는 공간이다.  낮은 주소부터 채워진다. 영역보다 크기가 커지면 overflow가 일어날 수 있다.

Stack에는 지역 변수, 독립적으로 실행되는 함수의 호출 매개변수나 return 결과값 등이 저장된다. 높은 주소부터 채워지며 overflow 발생 위험이 있다.

</br>

</br>

### Process의 상태

- **실행** - cpu를 할당받고, 기계어 멍령을 수행하고 있는 프로세스의 상태이다.

- **준비 상태** - cpu만 할당 받으면 바로 실행 가능한 대기상태이다.

  OS는 준비 Process들을 줄세워서 대기시키기 위해 ready queue를 만들고, queue의 front에 cpu를 할당한다.

- **봉쇄 상태** - cpu를 할당받더라도, 프로세스를 수행 못하는 상태이다. interrupt가 들어와 있을 때에 이 상태에 진입한다.

**준비 ⇒ 실행**  : 이미 실행되던 process가 block 상태가 되었거나 , 종료되는 상태에 진입 가능하다.

</br>

</br>

### Process 동기화

### **Critical Section**

: 동일한 자원을 동시에 접근하는 작업을 실행하는 코드 영역. → race condition이 일어날 수 있다.

### Critical Section Problem

한 thread가 접근했을 경우, 다른 thread는 접근이 배제되어야 한다.

**Requirements ( 해결을 위한 기본 조건 )**

1. Mutal Exclusion ( 상호 배제 )

   process p1이 CS에서 실행중이라면, 다른 process들은 접근이 불가능하다.

2. Progress

   CS에서 실행중인 process가 없고, 별도의 동작이 없는 process들은 CS 진입 후보가 될 수 있다.

3. Bounded waiting (한정된 대기)

   Process 1이 CS 진입 신청 후 부터 받아들여질때까지 다른 process들이 CS에 진입하는 횟수는 제한이 있어야 한다. 왜냐하면 무한정 대기 상황이 된다면 계속해서 한 프로세스만 들어가는 경우가 생길 수 있고, 그럼 다른 프로세스에 대해서 starvation이 발생할 수 있기 때문이다.



**</br>**



**해결책**

1. LOCK → 시간 효율성이 떨어진다.

   HW기반 해결책. 동시 공유 자원에 접근하는 것을 막기 위해 CS에 진입하는 process는 LOCK(MUTEX)을 획득하고 CS를 빠져나올 때 LOCK를 방출하며 동시 접근이 불가능하게 한다.

2. Semaphore

   1. Counting Semaphore

      : 가용한 개수를 가진 자원에 대한 접근 제어용이다. 자원의 개수로 Semaphore를 초기화하고, 자원을 사용하면 —; 방출하면 다시 ++;

   2. Binary Semaphore

      : 0 또는 1개만 접근할 수 있게 하는것. Mutex가 해당된다. 다중 프로세스들 사이의 CS 문제를 해결하기 위해 사용된다.

   단점

   Busy Waiting( 바쁜 대기 )

   : 계속 진입을 위해서 프로세스가 진입 시도 코드를 수행한다면, 이것 또한 오버헤드가 생길 수 있다. 그러므로 진입 시도를 실패한 process에 대해서 Block 시킨 뒤에, CS에 자리가 나면 깨워서 진입시킨다.

```cpp
do{
	flag[i] = true;
	turn = j;
	while(turn==j && flag[j]);
	critical section...
	
	flag[i] = false;
	remainder section...
}while(1);
```

Peterson's algorithm

: turn / flag로 CS에 들어갈 process/thread를 결정한다.

turn → 어떤 flag가 CS에 들어갈 차례인가? ( turn 으로 mutal exclusion 적용)

flag → 공유 자원 사용 요청을 표현.