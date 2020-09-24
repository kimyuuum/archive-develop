# Bubble sort

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

------

```cpp
for(int i=0; i<n; i++){ 
	for(int j=1; j<n-i; j++){ 
	*// i개는 이미 뒤에 정렬되어있다.*
		if(arr[j-1] > arr[j]){
		 swap(arr[j-1],arr[j]); 
		} 
	} 
}
```

Bubble sort를 이용하면, 이미 정렬 되어있는 상태라도 계속 체크를 하게 된다.

=> sorted flag를 사용하면 개선 가능하다.

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