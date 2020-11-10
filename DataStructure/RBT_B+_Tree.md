# Red Black Tree



### RBT?

red black tree에 data를 저장하면, 삽입 삭제 검색 모두 O(logN)만에 수행 가능하다.

⇒ 동일한 노드의 개수를 가지고 있을 때 최대한 depth를 줄이는게 중요하다.

### Property

1. Root Property

    root node의 색은 black이다.

2. External Property

    모든 leaf node는 black이다.

3. Internal Property

    어떤 노드의 색이 red이면, 자식은 black이다. (No Double Red)

4. Depth Property

    ⇒ 루트노드부터 leaf node까지의 단순 경로 상에 있는 black node의 개수는 모두 동일하다.

### Insertion

- BST 특성을 유지하며 삽입한다. Black height의 변동을 최소화하기 위해 삽입노드의 색은 RED이다
- Property를 위배하는 경우 노드의 색을 조정해야 한다.
    1. Restructuring
    2. Recoloring

### Restructuring

현재 insert된 node의 uncle node의 색에 따라 조정 방법이 달라진다. 만약  uncle node가  black일 경우  restructring하고,  red recolor일 경우 recoloring한다. 

현재 insert된 node, 부모 노드, 그리고 grand parent node를 가지고 진행한다.

1. 위 세 노드를 오름차순으로 정렬한다.
2. 정렬 후 가운데 노드를 부모 노드로 지정하고, 나머지 두 개는 자식 노드로 설정한다.
3. 올라간 가운데 tree를 black으로, 나머지를 red로 변경한다.

### Recoloring

현재 insert된 node의 부모와, 그 형제를 black으로 하고, 부모의 부모를 red로 바꾼다.  Grand parent가 root node가 아닐 경우, double red가 발생할 수 있다.

⇒ recoloring , restructuring을 통해서 해결하자.

만약 double red가 발생한 경우, grand parent의 형제 노드 색을 보고, 둘중 하나를 다시 결정하면 된다. restructuring을 수행 할 경우 subtree에 영향이 없으니까 마무리 된다.

두 수행 결과 모두 O(1)만에 수행된다. 하지만 어떤 노드를 삽입 후 수행하는것이기 때문에 O(logn)이 걸린다.



# B+ Tree



키에 의해 각각 식별되는 레코드의 효율적 삽입, 삭제, 검색을 통해 정렬 데이터를 표현하기 위한 트리 구조이다. 데이터가 순차적으로 처리되어야 할 때 사용한다.
모든 레코드들은 트리의 최하위 레벨에 정렬되어 있고, 트리 내부 블록에는 Key만 저장된다. DB의 인덱싱을 진행할 경우, 위 자료 구조를 사용한다.