# Hash Table



### Hash Table?

hash table은 key를 사용하여 value를 저장하는 구조이다. 

`function(key) = value`

key로 value를 찾는데 O(1)이 소요된다.

Data의 삽입 삭제도 매우 빠르다. 하지만 무조건 O(1)은 아닌데, 이는 Collision 발생 가능성 때문이다.

</br>

### Feature

- 1:1은 거의 Array와 다를 바가 없다. 하지만 Collision이 늘어날수록 O(N)에 가까워진다.

    ⇒ Collision을 최소화 하고, 대응을 어떻게 할 것인지가 매우 중요하다.

</br>

**example**

```
key : 이름
value : 번호
size : 16
function("John Smith")
-> 해시함수 내에서 해당 키 값을 size로 나눠서 index를 반환한다. 해당 위치에 value를 저장한다.
```



</br>

## Collision

- hash table은 충돌 문제가 발생할 수 있다. idx가 중복되는 경우가 생기기 때문이다.

해결 방법

### Separate Chaining

JDK 내부에서도 사용되는 방식이고, linked list를 이용합니다.

각 index에 data를 저장하는 linked list에 대한 포인터를 가지는 방식입니다. 충돌이 발생할 경우, 해당 Index에 연결되어있는 연결 리스트의 크기를 늘려 추가합니다. 그러므로 데이터 추가 시 제약사항이 적습니다.

Java8 HashMap은, index에 node가 8개 이하일 경우에는 연결 리스트를, 그 이상은 tree 구조를 사용합니다. 또한, 노드 수에 따른 구조의 변경 시 크기의 차이가 2 이상 발생할때, 서로 전환합니다. (8과 6) 차이를 1로 두면, 빈번하게 삽입 삭제가 발생할 경우 구조를 바꾸는데에 오버헤드가 더 크기 때문입니다.

- Time Complexity

    Linked List - E(N/M)

    Tree - E(log N/M)

### Open Addressing

Index가 충돌 시, 바로 그 다음 index를 탐색하여 비어있을 경우 그곳에 삽입합니다. linked list와 같은 추가 메모리 공간을 사용하지 않습니다. ⇒ hash table의 빈 array 공간을 사용합니다. 

**Linear Probing**

만약 A가 1번 Index에 저장되어있는데, B도 1번 Index에 저장해야 하는 상황이라면 B는 2번 Index를 탐색합니다. 그리고 만약 해당 공간이 비어있다면, 그곳에 B의 value를 저장합니다. 만약 2번 공간도 비어있지 않다면 선형 탐색을 통하여 빈 공간을 찾습니다.

⇒ return하는 경우는, 빈 공간을 찾았거나, 빈 공간을 찾지 못하여 다시 원래의 인덱스로 돌아오는 경우 두 유형이 존재합니다.

**Resizing**

Open Addressing은 고정 크기 배열을 가지고 선형 탐색을 사용하기 때문에, 확장이 필요한 경우가 존재합니다. 더 큰 버킷을 가지는 Array를 생성하고, 그 Array에 현재 가지고 있는 배열을 모두 복사한 뒤 새로운 배열을 사용하여 탐색합니다.

**Data 검색**

해시 함수에 의해 나온 index에 접근한다. 만약 해당 index에 원하는 값이 없다면, 순차적으로 다음 index를 탐색하여 값을 찾거나, 모두 다 탐색한 경우 종료합니다.

**Data 삭제**

해당 index에 값이 존재하여 직접적으로 삭제하는 경우도 있지만, open addressing을 사용하여 다음 Index에 값이 저장된 경우도 존재합니다. 이럴 때에는, 값을 삭제하고 해당 빈 공간을 그냥 비우는 것이 아니라, 다음에 저장된 index를 탐색할 때 에러를 방지하기 위해 DEL과 같은 임의의 표시를 해 문제 없이 탐색할 수 있게 합니다.

`Open Addressing은 연속된 공간을 사용하기 때문에 Separate Chaining보다 캐싱 효율이 훨씬 좋다. 버킷을 계속 사용하기 때문에 resize 시기도 느리다.`



</br>

</br>