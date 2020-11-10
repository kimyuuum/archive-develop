# Stack / Queue

</br>

## **Stack**

선형 자료구조.

Last In First Out (LIFO) 자료구조를 가지고 있다.

DFS 진행 시 자주 사용하는게 좋다.

일의 실행순서를 기록해두었다가, 반대로 출력하는 경우 사용할 수 있다. 

→ 일이 실행될때마다 stack에 차례로 push했다가, 모두 실행 후 pop하면 된다.

**활용 - 일의 실행순서가 반대로 필요한 경우.**

⇒ 후위 표기 연산, backspace key, 진법 변환 ( 나머지를 stack에 저장하여 활용한다 ) , 문자열 뒤집기.

### Time Complexity

삽입, 삭제, 검색(top) - O(1)만에 수행 가능하다.

내부적으로는 vector, deque, list container의 구조로 구현이 되어있으나, stack으로 포장한것이다.

```jsx
s.push();
s.pop();
s.top();
//등이 사용된다.

Stack{
	T[] stack;
	top = -1;

	push(T data){
		stack[++top] = data;
	}
	
	T pop(){
		return stack[top--];
	}
	
	T top(){
		empty check;
		return stack[top];
	}
	
	int size(){
		return top+1;
	}
}

```

### Stack을 구현한다면?

1. Array 
    - Top 포인터로 index 접근이 가능하기 때문에 속도가 빠르다.
    - 정적 크기 할당으로, 한정적인 단점이 있다.
2. 단방향 linked list
    - head node에서 Push/Pop을 한다.
    - array에 비해 추가적인 메모리를 사용하지만, 동적 확장이 가능하다.

</br>

</br>

## **Queue**

선형 자료구조.

First In First Out (FIFO) 자료구조를 가지고 있다.

삽입 : enqueue

삭제 : dequeue 

맨 앞 자료 : peekFront

맨 뒤 자료 : peekRear

### 활용

1. Batch Process
    - cpu가 하나의 작업을 처리하기 시작하면 다른 작업은 실행되고 있는 작업이 끝날때까지 대기 상태에 있어야 한다.
2. Process Ready Queue
3. Scheduling
4. 프린터 출력 처리
5. 대기열 System
6. BFS

### Time Complexity

: 삽입, 삭제, 조회 모두 O(1)

주로 BFS 진행 시 사용하는게 좋다. 

```jsx
q.push();
q.pop();
q.front();
q.back();

Queue{
	T[] queue;
	front = 0;
	rear = 0;
	
	qush(T data){
		queue[rear++] = data;
	}
	
	T pop(){
		empty check;
		return queue[front++];
	}
	
	T peekFront(){
		return queue[front];
	}
	
	T peekRear(){
		return queue[rear];
	}
	
	int size(){
		return rear;
	}

};

```

</br>

</br>

## Deque

큐와 스택 둘 다로 활용 가능하다.

선형 자료구조.

LIFO FIFO 가 가능하다.

add First / Last 

pop First / Last

peek Head / Tail

### Time Complexity

앞/뒤 모두 삽입,삭제,조회 O(1) 수행 가능하다.

```cpp

Deque{
	T[] deque;
	head = mid;
	tail = mid;
	
	addFirst(T data){
		deque[--head] = data;
	}	
	
	addLast(T data){
		deque[tail++] = data;
	}
	
	T removeFirst(){
		empty check;
		return deque[head++];
	}
	
	T removeLast(){
		empty check;
		return deque[--tail];
	}
	
	T peekHead(){
		empty check
		return deque[head];
	}
	
	T peekTail(){
		empty check
		return deque[tail-1];
	}

};

```