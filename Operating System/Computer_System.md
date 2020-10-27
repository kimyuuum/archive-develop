
# Computer System

**1. Stack**
- 함수 호출시 함수의 수행을 마치고 복귀할 주소 및 Data를 임시 저장한다.
</br>

**2. Data**
- 전역변수 등 프로그램이 사용하는 변수 및 데이터를 저장한다.
</br>

**3. Code**
- 실행 파일에 담겨져 있는 코드들이 저장된다.
</br>

### 작동 개요

cpu는 현재 수행해야 할 메모리 주소의 명령을 처리한다. 메모리 주소를 가지고 있는 레지스터는 Program Counter라 칭한다.

```c++
if (program counter 가 메모리 주소 중 OS가 존재하는 부분을 가리키면)
  cpu가 kernel 모드에서 수행중이라고 한다.
else
  cpu가 사용자 모드에서 수행중이라고 한다.
```
</br>

### System call
사용자 모드에서 특권 명령 관련 요청을 수행하고자 할 때, OS에게 대행을 요청하는 경우이다.

### 실행 개요
![image](https://user-images.githubusercontent.com/46887352/97271117-85cc5a80-1873-11eb-9419-4a9d217c560c.png)
</br>
</br>
![image](https://user-images.githubusercontent.com/46887352/97271146-8e249580-1873-11eb-90da-37960056774b.png)
</br>

### Kernel의 공간 구성
**Stack**

함수 호출 / 복귀 위치를 저장해주는 공간이다. kernel은 수행중인 프로세스마다 스택을 두어서 관리한다. 
프로그램이 실행되어 자신의 코드 내의 함수는 자신의 스택, System call 등의 호출은 커널 스택을 사용한다.
</br>

**Data**

자원 관리 자료 구조를 저장한다. 현재 수행중인 주체 프로그램을 `process`라고 부른다.
각 프로세스의 상태와 메모리 정보 관리를 위해 PCB가 존재한다.
</br>

**Code**

System call 및 인터럽트 처리 부분을 포함한다.
자원 관리가 핵심이다.

</br>
</br>
