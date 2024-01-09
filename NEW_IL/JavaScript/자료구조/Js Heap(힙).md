## 힙이 멀까
일종의 완전 이진 트리다.
주로 우선순위 큐를 구현 시 베이스가 되는 자료구조로 쓰인다.
트리 구조이기 때문에 삽입과 삭제에 O(logN)의 시간이 소요된다.

힙은 최대힙(Max Heap) 또는 최 소힙(Min Heap)으로 구분가능하며, 빠른 시간 안에 최대값 또는 최소값을 찾아낼 수 있다.
주로 배열을 이용해 힙을 구현할 수 있고, 보통 다른 언어들의 경우에는 heap구조 자체를 기타 라이브러리를 통해 기본적으로 제공하는 경우가 많다.

JAVA같은 경우에는 PriorityQueue가 있으며, python3는 heapq이나 힙을 구조화 시켜주는 heapify등이 있지만 js는 지원해주지않는다,,

### 힙에서 부모 - 자식 간 관계
힙은 이진 트리이기 때문에 부모와 자식 노드가 발생하는데, 힙같은 경우엔 일반적인 완전 이진 트리와는 다르게 반정렬 상태를 유지한다. 
이는 최대힙이면 큰 값이 부모 노드쪽에, 최소힙이면 작은값이 부모노드 쪽에 배치되는 것만 유지하고 왼쪽 자식과 오른쪽 자식은 부노 노드보다 작은 값을 유지하기만 하면 된다.

## 배열을 이용해 힙을 구현해보자!!
```js
class Heap {
	constructor() {
		this.heap = [ null ];  //첫 원소는 사용 x
	}
}
```
배열의 첫 원소는 사용하지 않기때문에 부모와 자식 간 다음의 관계가 성립된다.
완전 이진트리의 일종이기 때문에 Binaray Search tree 에서의 부모-자식 관계와 유사하다.
+ 왼쪽 자식의 index = `부모 index * 2*
+ 오른쪽 자식의 index = `(부모 index * 2) + 1*`
+ 부모의 index =  `Math.floor(자식의 인덱스 /)`


### 삽입
삽입은 마지막 노드에 들어온 값을 push해 삽입한다. 
이때 재귀적이든 반복문을 돌리든 부모노드를 확인하면서 들어온 값이 부모노드보다 작은지 여부를 확인하며 위치를 교환해주며 정렬해준다.
최소힙으로 구현할 때의 삽입과정을 살펴보자잉

```js
heapPush(value) {
	this.heap.push(value);
	let curIdx = this.heap.length -1;
	let parIdx = (curIdx / 2) >> 0;
	
	while(curIdx > 1 && this.heap[parIdx] > this.heap[curIdx]) {
		[ this.heap[parIdx], this.heap[curIdx] ] =[ this.heap[curIdx],this.heap[parIdx] ];
		curIdx = parIdx;
		ParIdx = (curIdx / 2) >> 0;
	}
}

```

### 삭제
힙에서는 최소힙이든 최대힙이든 로트 노드가 항상 먼저 배출되어야 한다. 배출 후 생기는 빈자리는 가장 마지막 노드, 배열에서 제일 뒤에있는 값을 가져온다. 그리고 다시 루트노드로부터 재정렬을 실행해준다.
```js
heapPop(){
const min 
  const min = this.heap[1];	// 배열 첫 원소를 비워두므로 root는 heap[1]에 항상 위치한다.
  if(this.heap.length <= 2) this.heap = [ null ];
  else this.heap[1] = this.heap.pop();
  // 배열 마지막 원소를 root 위치에 먼저 배치하는 과정이다.
  // if-else로 분기되는 이유는 추후 heap이 비었는지 아닌지 확인하기 위해 size 체크 함수를 만들때 -1을 통해 0을 만들어주기 때문.
  
  let curIdx = 1;
  let leftIdx = curIdx * 2;
  let rightIdx = curIdx * 2 + 1;
  
  if(!this.heap[leftIdx]) return min;
  // 왼쪽 자식이 없다는 것은 오른쪽 자식도 없는, 즉 루트만 있는 상태이므로 바로 반환!
  if(!this.heap[rightIdx]) {
    if(this.heap[leftIdx] < this.heap[curIdx]) {
      [ this.heap[leftIdx], this.heap[curIdx] ] = [ this.heap[curIdx], this.heap[leftIdx] ];
      // 오른쪽 자식이 없다면 왼쪽 자식하나만 있다는 것을 의미한다.
    }
    return min;
  }
  
  // 위에 조건에 걸리지 않는 경우 왼쪽과 오른쪽 자식이 모두 있는 경우이다.
  // 따라서 현재 노드가 왼쪽 또는 오른쪽 보다 큰 지 작은지를 검사하며 반복한다.
  while(this.heap[leftIdx] < this.heap[curIdx] || this.heap[rightIdx] < this.heap[curIdx]) {
    // 왼쪽과 오른쪽 자식 중에 더 작은 값과 현재 노드를 교체하면 된다.
    const minIdx = this.heap[leftIdx] > this.heap[rightIdx] ? rightIdx : leftIdx;
    [ this.heap[minIdx], this.heap[curIdx] ] = [ this.heap[curIdx], this.heap[minIdx] ];
    curIdx = minIdx;
    leftIdx = curIdx * 2;
    rightIdx = curIdx * 2 + 1;
  }
  
  return min;

}
```
### 전체코드
```js
MinHeap {
    constructor() {
        this.heap = [ null ];
    }
    
    size() {
        return this.heap.length - 1;
    }
    
    getMin() {
        return this.heap[1] ? this.heap[1] : null;
    }
    
    swap(a, b) {
        [ this.heap[a], this.heap[b] ] = [ this.heap[b], this.heap[a] ];
    }
    
    heappush(value) {
        this.heap.push(value);
        let curIdx = this.heap.length - 1;
        let parIdx = (curIdx / 2) >> 0;
        
        while(curIdx > 1 && this.heap[parIdx] > this.heap[curIdx]) {
            this.swap(parIdx, curIdx)
            curIdx = parIdx;
            parIdx = (curIdx / 2) >> 0;
        }
    }
    
    heappop() {
        const min = this.heap[1];	
        if(this.heap.length <= 2) this.heap = [ null ];
        else this.heap[1] = this.heap.pop();   
        
        let curIdx = 1;
        let leftIdx = curIdx * 2;
        let rightIdx = curIdx * 2 + 1; 
        
        if(!this.heap[leftIdx]) return min;
        if(!this.heap[rightIdx]) {
            if(this.heap[leftIdx] < this.heap[curIdx]) {
                this.swap(leftIdx, curIdx);
            }
            return min;
        }

        while(this.heap[leftIdx] < this.heap[curIdx] || this.heap[rightIdx] < this.heap[curIdx]) {
            const minIdx = this.heap[leftIdx] > this.heap[rightIdx] ? rightIdx : leftIdx;
            this.swap(minIdx, curIdx);
            curIdx = minIdx;
            leftIdx = curIdx * 2;
            rightIdx = curIdx * 2 + 1;
        }

        return min;
```