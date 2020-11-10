# Sort

## Bubble Sort

**매번 연속된 두개의 인덱스를 비교하여 조건에 맞게 위치를 바꾸는 정렬.**

</br>

### **Time Complexity**

- O(N^2)

### **Space Complexity**

- O(N)

</br>

</br>

### **FLOW**

1. 현재 인덱스 값과 바로 이전 인덱스 값을 비교한다.
2. 이전 idx에 있는 원소가 더 크면 둘의 위치를 변경한다.
3. 현재 idx가 더 크면, 다음 idx로 넘어가서 두개를 다시 비교한다.

```cpp
for(int i=0; i<n; i++){ 
	for(int j=1; j<n-i; j++){ 
	// i개는 이미 뒤에 정렬되어있다.
		if(arr[j-1] > arr[j]){
		 swap(arr[j-1],arr[j]); 
		} 
	} 
}
```

Bubble sort를 이용하면, 이미 정렬 되어있는 상태라도 계속 체크를 하게 된다.

=> `sorted flag를 사용하면 개선 가능하다.`

</br>



중간에 한번이라도 원소의 교환이 일어나면 flag의 상태를 변경한다. 바뀌지 않았으면, 교환이 일어나지 않은 `정렬된 상태`이다. 만약 정렬된 상태의 배열이 들어오면 Θ(n)만에 수행 가능하다.

```cpp
for(int i=0; i<n; i++){
	bool sorted = true;
	for(int j=1; j<n-i; j++){
	 if(arr[j-1] > arr[j]){
		swap(arr[j-1],arr[j]);
		sorted = false; 
		} 
	} 
	if(sorted){ break; } 
}
```

</br>

</br>

---


## Selection Sort

</br>

**해당 원소에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 선택하는 정렬**

### **Time Complexity**

- O(N^2)

### **Space Complexity**

- O(N)

</br>

### **FLOW**

1. 주어진 원소 중에서 가장 작은 원소를 찾는다.
2. 그 값을 맨 앞에 위치한 원소와 교체한다.
3. 맨 처음 위치를 제외한 나머지 리스트에 대하여 반복한다.


```cpp
for(int i=0; i<n-1; i++){
 *//한개가 남을때까지 반복한다.*
	int target = i; 
	for(int j=i+1; j<n; j++){
	 if(arr[target] > arr[j]){
		 target = j; 
		}
	} 
	swap(arr[target],arr[i]); 
}
```

자료 이동 횟수는 미리 결정된다. unstable한 정렬이다.

5(1) 4 5(2) 2 3

=> 2 4 5(2) 5(1) 3

첫번째 5가 정렬 후 뒤로 가기 때문에, **값이 같은 레코드가 있는 경우** 상대적 위치가 변경될 수도 있으므로 unstable한 정렬이다.

</br>

</br>

------


## Insertion Sort

이미 정렬 되어있는 배열에 한 원소를 추가하는 경우에, 제 자리를 탐색해서 해당 자리에 삽입을 해서 배열이 정렬 상태를 계속 유지하면서 크기를 늘리는 정렬입니다.

Selection / Bubble Sort는 크기가 N인 배열에서 시작했다면 Insertion Sort는 1부터 크기가 증가합니다.

- 배열이 정렬되어있는 상태라면, while이 한번도 수행되지 않아서 for문은 상수 시간이 소요됩니다.
- for문은 n-1번 순환하므로 O(N)입니다.

</br>

### Time Complexity

O(N^2), 최선의 경우 O(N)

### Space Complexity

O(N)

stable한 sort이다.

</br>

### FLOW

1. 2번째 index부터 시작한다.
2. 그 앞 원소들과 비교해서, 삽입 위치를 지정하고 자료를 뒤로 밀어낸 뒤에 삽입합니다.


```cpp
for(int i=1; i<n; i++){
	int j = i-1;
	while(j >= 0 && arr[j] > arr[j+1]){
		swap(arr[j],arr[j+1]);
		j--;
	}
}
```



</br>

</br>


------


## Merge Sort

입력을 반으로 나누고, 전 / 후반부를 독립적으로 정렬한다. 이 두개를 Merge해서, 정렬 배열을 얻는다.

### Time Complexity

- O(nlogn)

크기가 8인 배열은, 최종적으로 N/8 크기가 8개 생긴다. 즉, 3번만에 배열의 길이가 1인 것을 만들어낸 것인데, 분할 과정은 **매번 절반씩** 감소한다. 그러므로, 밑이 2인 logN만큼 반복한다.

각 분할 별로 merge를 진행한다. 최대 N, 평균 N * logN = NlogN이 된다.

### Space Complexity

O(logN)

Stable sort이다.

</br>

</br>

### FLOW

1. base condition ⇒ size가 0 또는 1이면 이미 정렬된 것으로 본다.
2. 정렬되지 않은 리스트를 절반으로 쪼개서, 비슷한 크기의 두 부분 리스트로 나눈다.
3. 재귀적으로 merge sort를 실행한다.
4. 두 부분 list를 다시 merge한다.

Divide → Conquer → Combine

추가 임시 배열이 필요하다. 실제로 정렬이 이루어지는 시점은, 두 list가 merge 될 때이다.

```cpp
void merge(int left,int mid, int right){
	vector<int> temp;
	int i = left;
	int j = mid+1;

	while(i <= mid && j <= right){
		if(arr[i] < arr[j]){
			temp.push_back(arr[i]);
			i++;
		}else{
			temp.push_back(arr[j]);
			j++;
		}
	}

	while(i <= mid){
		temp.push_back(arr[i]);
		i++;
	}
	
	while(j <= right){
		temp.push_back(arr[j]);
		j++;
	}
	
	int cnt = 0;

	for(int idx = left; idx <= right; idx++){
		arr[idx] = temp[cnt++];
	}
}

void mergesort(int left, int right){
	if(left < right){ //size > 1 
		int mid = (left + right) / 2;
		mergesort(left,mid);
		mergesort(mid+1,right);
		merge(left,mid,right);
	}
}
```





</br>

</br>

------


## Quick Sort



평균 성능이 좋아 가장 빈번하게 쓰이는 정렬이다.

### Time Complexity

- 평균 O(NlogN), 최악 O(N^2) ( 이미 정렬되었거나, 역순인 경우)

### Space Complexity

- O(logN)

unstable한 sort이다.

</br>

### FLOW

1. 배열의 가장 왼쪽 또는 오른쪽을 특정 pivot으로 설정한다.

2. pivot보다 작은 원소는 왼쪽, 큰 원소는 오른쪽에 배치하여 한번 정렬을 완료한다.

3. pivot을 제외하고 나뉘어진 두 배열에 대해서 다시 재귀적으로 pivot을 설정하여 반복한다.

   ⇒ 부분 list들이 더이상 분할 불가할 때 까지 반복한다. (size == 0 or 1)

- 전체 list를 2개로 분할한다 ⇒ 각각의 부분 list에 대해서 다시 quick sort를 진행한다.
- **quick sort는 merge sort와는 다르게, 리스트를 비균등하게 분할한다.**


### 분할 정복

문제를 작은 2개의 문제로 분리하고, 각각을 해결한 다음 결과를 모아서 원래의 문제를 해결한다.

```cpp
int partition(int left, int right) {
  int pivot = arr[left];
  int low = left + 1;
  int high = right;

  while (low <= high) {
    while (arr[low] <= pivot && low <= right) {
      low++;
    }
    while (arr[high] >= pivot && high > left) {
      high--;
    }

    if (low > high) {
      swap(arr[left], arr[high]);
    } else {
      swap(arr[low], arr[high]);
    }
  }

  return high;
}

void quicksort(int left, int right) {
  if (left < right) {
    int q = partition(left, right);
    quicksort(left, q - 1);
    quicksort(q + 1, right);
  }
}
```

</br>



### Quick Sort 개선

1. Random 분할

   pivot을 0 ~ n-1 범위의 난수로 선택한다. 난수의 위치가 배열 제일 오른쪽 원소와 위치를 바꾸고, quick sort를 진행한다.

2. 삽입 정렬 활용하기

   삽입 정렬은 크기가 작은 배열에서 효율이 매우 좋다. 추가적인 메모리를 필요로 하지도 않는다.

   작은 구간에서는 삽입 정렬을 활용하고, 재귀의 깊이를 줄인다.

3. 세 값의 중위

   1. 가장 왼쪽
   2. 가장 오른쪽
   3. 중간 값

   ⇒ 이 세 값을 정렬하고, 가장 작은 값을 왼쪽, 가장 큰 값을 오른쪽, 그리고 중간 값을 arr[right - 1]에 배치한 뒤에 pivot으로 삼아 quick sort를 진행한다.

   정렬 구간을 arr[left+1] ~ arr[right-2]로 줄일 수 있다. 재귀의 깊이도 줄일 수 있고, 분할도 대부분 중앙에서 이루어진다.



</br>

</br>

------


## Heap Sort



최대 / 최소값을 구할 때, 혹은 최대 K만큼 떨어진 요소들을 정렬할때에 쓰인다.

### Heap?

이진 트리 구조를 가지고, 맨 아래층을 제외하고는 모두 채워져 있어야 하는 완전 이진 트리 형태이다. 맨 아래층은 왼쪽부터 채워져야 한다. 각 node의 값은 자신의 자식 값보다 작거나(min Heap) 커야 한다.(max heap)

### Time Complexity

- O(nlogn)

### Space Complexity

- O(1)

unstable한 sort이다.

### Property

1. Order Property

   Max Heap을 구성하는 경우, root값이 지속적으로 최댓값을 가진다.

   Min Heap을 구성하는 경우, root값이 지속적으로 최솟값을 가진다.

   → 최대 / 최소값을 쉽게 추출할 수 있는 구조이다.

2. Structural Property

   Heap은 항상 완전 이진트리 형태여야 한다.

### Heap vs 균형 이진 트리

물론 균형 이진트리에서 더 많은 기능들을 제공하지만, 최대 또는 최소 값을 구하거나 삽입 삭제를 위해서는 Heap을 사용하는것이 더 효과적이다.

</br>



### Heapify

만약 자식을 가지는 노드가 있다면, 역순으로 heapify한다. 자식 노드를 0,1,2가 가지고 있다면, 이를 2부터 호출하여 heapify를 진행한다.

```cpp
void heapify(int idx, int size) {
  int target = idx;
  int left = idx * 2 + 1;
  int right = idx * 2 + 2;

  if (arr[left] > arr[target]) {
    target = left;
  }
  if (arr[right] > arr[target]) {
    target = right;
  }

  if (idx != target) {
    swap(arr[idx], arr[target]);
    heapify(target, size);
  }
}

void heapsort(int size) {
  for (int i = (size - 1) / 2; i >= 0; i--) {
    heapify(i, size);
  }
}
```

</br>

### Max Heap

**Insertion**

- 힙에 새로운 요소가 들어오면 우선 가장 마지막 인덱스에 삽입합니다. 이진트리 구조이기 때문에, 부모 노드는 해당 idx의 / 2 가 된 값입니다. 부모 노드부터 차례대로 크기를 확인해주면서, 만약 새로운 요소가 더 큰 값을 가지고 있다면 swap을 수행합니다. 이 과정을 루트 노드까지 도달하거나, 또는 큰 원소를 만나기 전까지 반복합니다.

**Deletion**

- 가장 끝에 위치한 leaf node와 root node의 순서를 바꿉니다. 자식과의 크기 비교를 통해서 원하는 조건일때까지 반복합니다.

```cpp
void insertion(int idx){
	int now = idx;
	while(idx >= 1){
		int parent = idx / 2;
		if(arr[parent] < arr[now]){
			swap(arr[parent],arr[now]);
			now/=2;
		}else{
			break;
		}
	}
}

void deletion(){
	int target = 1;
	arr[1] = arr[n];
	while(target * 2 + 1 >= n){
		int left = target * 2;
		int right = target * 2 + 1;

		if(arr[left] < arr[right]){
			swap(arr[target],arr[right]);
			target = right;
		}else{
			swap(arr[target],arr[left]);
			target = left;
		}
	}
}
```

[알고리즘 스터디 - 11(Sort - 힙 정렬(Heap Sort)](https://xmfpes.github.io/algorithm-study/daily-algorithm-11/)



</br>

</br>


------


## Topology Sort



방향이 있는 그래프에서, 정점들을 정렬하는 방법이다. 방향 그래프에서 간선으로 주어진 정점 간에 선후관계를 위배하지 않도록 나열하는 정렬이다.

### DAG (Directed Acyclic Graph)

방향성이 있고, 순환 사이클이 없는 그래프를 뜻한다. 만약 그래프 내에 사이클이 있는 경우에는 올바른 위상 정렬이 불가능하다.

### Time Complexity

+ O(V+E)

</br>



### FLOW

1. 가장 앞에 오는 원소는 자신보다 앞에 위치하는 원소가 없어야 한다.  `Indegree == 0`
2. 매 순간마다 들어오는 간선이 없는 정점을 제거하며 정렬한다.

정점과 간선을 지울 필요 없이 미리 indegree의 개수를 저장했다가, 매번 뻗어나가는 정점들의 Indegree 값을 감소시킨다. indegree가 0인 정점을 구하기 위해 매번 확인하는 대신, 목록(Queue)을 따로 저장하고 있다가 직전 제거 정점에서 연결 정점을 추가한다.


### Sorting

위상 정렬은 visited 배열이 필요가 없다. 모든 정점은 Indegree가 0이 되는 순간이 딱 한 번씩 밖에 없기 때문이다. 그래프에 사이클이 존재하는 경우, 애초에 Indegree가 0이 될 수가 없어 큐가 비게 된다.

1. 맨 처음, 모든 간선을 읽으며 Indegree 배열을 채운다.

2. `if(indegree[idx] == 0)` then q.push(idx);

3. 큐의 front에 있는 정점을 가져와서 위상 정렬 큐에 추가한다.

4. 해당 정점으로부터 연결된 모든 정점의 Indegree 값을 1 감소시킨다.

   → 연결 정점의 indegree가 0이 되면 q.push(idx);

5. 큐가 empty일 때 까지 3,4를 반복한다.

```cpp
#include <iostream>
#include <queue>
#include <vector>
using namespace std;

const int V = 20002;
vector<int> adj[V];
queue<int> q;
vector<int> res;

int indegree[V];
int n,m;

int main(){
	cin>>n>>m;
	for(int i=0; i<m; i++){
		int a,b;
		cin>>a>>b;
		adj[a].push_back(b);
		indegree[b]++;
	}
	
	for(int i=1; i<=n; i++){
		if(indegree[i] == 0){
			q.push(i);
		}
	}
	

	while(!q.empty()){
		int node = q.front();
		res.push_back(node);
		q.pop();
		
		for(int i=0; i<adj[node].size(); i++){
			int nextnode = adj[node][i];
			indegree[nextnode]--;
			if(indegree[nextnode] == 0){
				q.push(nextnode);
			}
		}
	}

	return 0;
}
```



</br>

</br>

------


## Counting Sort



**선형 시간에 정렬하기 위해 사용한다.**

정렬하고자 하는 원소들의 값이 O(N)을 넘지 않는 경우 가능하다. 원소 간의 비교 정렬이 아니고, 크기가 한정되어있는 데이터일 경우 사용한다.

ex) arr[1…n]이 k를 넘지 않는 자연수여야 한다. 그래야 원소를 훑고, 각각 몇번 나타났는지 확인 가능하다.

### **Time Complexity**

- O(N+K)
- K : 배열에서 가장 큰 값.
- 각 숫자가 나온 횟수를 세는 시간:  O(N)
- 다시 숫자를 원래 배열에 채워 넣는 시간:  O(N)
- 총 K번 반복 O(K)

### **Space Complexity**

- O(N+K)
- 정렬을 위한 배열의 길이 O(N) , 계수를 위한 배열의 길이 O(K)



</br>



### **FLOW**

1. 각 값마다 몇개가 있는지 counting한다.
2. 위에서 만든 배열의 누적 합을 구하여, 배열에 저장한다.
3. 값을 하나씩 주고, 1씩 빼준다.

- 숫자 크기에 따라 시간 복잡도가 매우 큰 영향을 받는다.



```cpp
	*#include <iostream>
	#include <vector>*
	using namespace std;

	const int MAX = 100;
	vector<int> v = {5, 5, 3, 4, 5, 1, 0, 4, 1, 3, 0, 2, 4, 2, 3, 0};
	int res[MAX];
	int c[10];

	int main() {
		for (int i = 0; i < v.size(); i++) {
			c[v[i]]++; 
		}
		
		for (int i = 1; i < 10; i++) {
			c[i] += c[i - 1]; 
		}
		
		for (int i = v.size() - 1; i >= 0; i--) {
			int idx = c[v[i]];
			res[idx] = v[i];
			c[v[i]]--; 
		}
		
		for (int i = 0; i < v.size(); i++) {
			cout << res[i] << " ";
		}
			
		return 0; 
	}
```


</br>

</br>
