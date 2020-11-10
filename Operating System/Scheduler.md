# Scheduler

---

process를 스케줄링 하기 위한 Queue의 종류.

1. Job Queue - 모든 process의 집합.
2. Ready Queue - cpu 할당을 받기 위해 준비하고 있는 process들의 집합.
3. Device Queue - Device I/O 작업을 대기하는 process의 집합.

</br>

### Long Term Scheduler

메모리는 한정적인데, 너무 많은 process가 한번에 올라올 경우 disk에 저장해야 한다. 이 중 어떤 process를 할당하여 ready queue로 보낼지 결정하는 역할을 한다.

메모리 ←Scheduling→ 디스크

process status : new → ready

</br>

### Mid Term Scheduler

여유 공간 확보를 위해 메모리 → Disk로 프로세스를 쫓아내는것을 의미한다. 너무 많은 process가 동시에 올라가는것을 방지하기 위해 사용되는 스케줄러이다.

</br>

### Short - Term Scheduler (CPU Scheduler)

cpu와 memory 사이의 스케줄링을 담당한다. ready queue에 존재하는 process중에 어떤 process를 실행시킬지 결정한다. process에 cpu를 할당시킨다.

ready → running → waiting → ready

1. **FCFS (First Come First Served)**

   가장 먼저 온 process가 cpu를 선점한다. 비선점 방식이며, process의 수행이 끝날때까지 다른 process는 선점이 불가능하다.

2. **SJF (Shortest Job First)**

   가장 짧은 프로세스 먼저 수행한다. 하지만 이렇게 되면 긴 프로세스는 starvation이 일어날 수 있다. 너무 배제되어도 좋지 않다.

3. **SRT (Shortest Remaining time First)**

   새로운 process가 도착할때마다 scheduling을 진행한다.

   그래서 burst time이 가장 짧은 프로세스먼저 실행한다. preemptive 방식이다. 하지만 계속해서 scheduling을 해서 오버헤드가 발생한다.

4. **Priority Scheduling**

   우선순위가 가장 높은 cpu에게 할당한다. 우선순위는 정수로 표현하고, 정수가 작을수록 우선순위가 높은 것이다.

   - Preemptive 방식 : 더 높은 우선순위의 process가 존재하면,  cpu를 선점한다.
   - Non - Preemptive 방식 : 더 높은 우선순위의 process가 도착하면 ready queue의 front에 삽입한다.

   Starvation → aging으로 해결한다. 너무 우선순위가 낮은 process도 계속해서 실행이 되지 않는다면 좋지 않은 방식이므로, aging을 통해서 적절하게 해결하자.

5. **Round Robbin**

   현대적인 CPU scheduling.

   각 process는 동일한 할당 시간을 가진다. 할당 시간이 지나면 process는 선점당하고, ready queue에 push된다. cpu burst time이 섞여있는 경우 가장 효율적이다.

   - response time이 빨라진다. 하지만 설정한 수행 시간이 너무 짧으면 context switch로 인한 오버헤드가 커지고, 수행 시간이 너무 길면 FCFS와 다를 바 없으므로 적절하게 정해야한다.

</br>

</br>