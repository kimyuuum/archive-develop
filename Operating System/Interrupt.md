# Interrupt



**주변 장치와 I/O 장치는, cpu나 memory와 달리 Interrupt 매커니즘을 통해 관리된다.**



### Interrupt의 이유

I/O연산은 cpu 연산보다 매우 느리다. cpu가 프로그램을 실행하고 있을 때, I/O 나 HW 등의 장치나 예외 상황이 발생하여 처리가 필요할 때, 마이크로 processor에게 알려 처리할 수 있도록 한다.

### HW Interrupt

하드웨어가 발생시키는 Interrupt. cpu가 아닌 다른 하드웨어 장치가, cpu에 어떤 사실을 알려주거나 서비스를 요청할 경우 발생한다.

### SW Interrupt

SW가 발생시키는 interrupt. SW가 스스로 interrupt line을 세팅한다.

ex) exception / system call.

Interrupt 발생을 위해 HW , SW는 cpu 내에 있는 인터럽트 라인을 세팅해서 발생시킨다. cpu는 명령 수행을 하기 전에, Interrupt line이 세팅되어있는지 검사한다.



### Process

- proc A가 디스크에서 어떤 데이터를 read 하라는 명령을 받은 경우

1. procA는 system call을 통해 interrupt를 발생시킨다.
2. 현재까지 수행 중이던 process A의 상태를 PCB(Process Control Block)에 저장한다. → 수행중이던 메모리 주소, 상태, 레지스터 값..
3. PC(Program Counter)에 다음에 실행할 명령의 주소를 저장한다.
4. Interrupt vector를 읽고 ISR(Interrupt Service Routine) 주소값을 얻어서, 점프해서 실행한다.
5. 해당 코드를 실행한다.
6. 완료 후, 대피시킨 register를 복원한다.
7. PC를 활용해서 이전 실행 위치로 복원시킨다.



### Interrupt와 특권 명령

- 명령어의 종류

1. 일반 명령 - memory에서 자료를 읽어오고, cpu에서 계산을 하는 등의 명령이고, 모든 프로그램이 수행 가능하다.
2. 특권 명령 - 보안이 필요한 명령. OS만 수행 가능하며, I/O 장치, 다른 장치를 접근하는 명령이다.



### Kernel vs User Mode

- kernel mode - os가 cpu의 제어권을 가지고 명령을 수행하는 mode. 일반 / 특권 둘 다 수행 가능하다.
- user mode - 일반 user program이 cpu 제어권을 가지고 명령을 수행하는 모드. 일반 명령만 가능하다.

만약 proc A가 disk 명령을 받은 경우, proc A는 PCB에 자신의 수행 기록을 저장해두고 system call을 발생 시켜서 kernel mode로 전환한다.