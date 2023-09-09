## 배열 관련 메소드

### sort
> 배열을 오름차순 내림차순으로 정렬한다.
```js
let arr = [5, 3, 2, 4, 6, 1];
console.log(arr.sort()); //[1, 2, 3, 4, 5, 6]
console.log(arr.sort((a, b) => b - a)); //[6, 5, 4, 3, 2, 1]
```

### join
> 배열을 문자열로 변환한다.
```js
arr.join(); // 구분자를 넣지 않으면 컴마가 포함되어 문자열로 합쳐진다.
arr.join('.');  // 구분자를 넣어주면 아이템 사이에 구분자를 넣어서 문장여로 합쳐진다.
```

```js
let arr = ['apple', 'banana', 'orange'];
console.log(arr.join()); // 'apple,banana,orange'
console.log(arr.join(' ')); //'apple banana orange'
```
### split
> 문자열을 배열로 변환한다.

```js
let arr = 'A,B,C,D';
console.log(arr.split(','));  //[A, B, C, D];
```
### reverse
> 배열의 아이템의 순서를 뒤집는다.

```js
let arr = [1, 2, 3, 4, 5, 6];

console.log(arr.reverse()); //[6, 5, 4, 3, 2, 1]
console.log(arr);  // [6, 5, 4, 3, 2, 1] 원래배열도 변경되어있다.
```

### splice
> 인덱스로 배열의 아이템을 삭제  
인덱스로 배열의 아이템을 여러개 삭제  
인덱스로 배열의 아이템을 삭제하고 해당 인덱스에 새로운 아이템 추가  
반환값은 삭제한 요소배열

#### 사용법
```js
arr.splice(인덱스, 삭제할 개수, 추가할 아이템...);
```

```js
let arr = [1, 2, 3, 4, 5];
let res = arr.splice(1, 3);

console.log(res);
// [2, 3, 4]
console.log(arr);
// [1, 5]
```

### slice
> 배열의 특정한 부분을 리턴한다.

```js
let arr = [1, 2, 3, 4, 5];
console.log(arr.slice(2)) //2부터 쭉 [3, 4, 5]
console.log(arr.slice(1,3)) //[2, 3]
```
### fill
> 배열의 시작 인덱스 부터 끝 인덱스 이전까지 정적 값 하나로 채운다.

```js
// 사용법
arr.fill(value[, start[, end]]); // 배열을 채울값, 시작 인덱스, 끝 인덱스
let arr = [1, 2, 3, 4];
console.log(arr.fill(0,2,4)); //[1, 2, 0, 0]
console.log(arr.fill(5, 1));  //[1, 5, 5, 5]
console.log(arr.fill(6));     //[6, 6, 6, 6]
```

### at
> 정수를 받아 해당 인덱스에 있는 요소를 반환한다.
> 양수, 음수를 모두 사용할 수 있으며, 음수는 마지막 배열부터 거슬러 올라온다.
```js
let arr = [1, 2, 3, 4, 5, 6];
console.log(arr.at(2)); // 3
console.log(arr.at(-2)); // 5
```

### find 
> 주어진 조건에 만족하는 첫번째 요소의 값을 반환한다.(없다면 undefined)
```js
let arr = [1, 2, 3, 4, 5, 6];
const found = arr.find((element) => element > 4);
console.log(found); // 5
```

### findLast
> 배열을 역순으로 돌아 주어진 조건에 만족하는 첫번째 요소의 값을 반환한다.(없다면 undefined)
```js
let arr = [1, 2, 3, 4, 5, 6];
const found = arr.findLast((element) => element > 4);
console.log(found); // 6
```

### findIndex
> 주어진 조건에 만족하는 첫번째 요소의 인덱스를 반환한다.(없다면 -1)

```js
let arr = [1, 2, 3, 4, 5, 6];
const isLargeNumber = (element) => element > 4;
console.log(arr.findIndex(isLargeNumber)); // 4
```

### findLastIndex
> 배열을 역순으로 돌아 주어진 조건에 만족하는 첫번째 요소의 인덱스를 반환한다.(없다면 -1)
```js
let arr = [1, 2, 3, 4, 5, 6];
const isLargeNumber = (element) => element > 4;
console.log(arr.findLastIndex(isLargeNumber)); // 5
```
### flat
> 모든 하위 배열 요소를 지정한 깊이까지 재귀적으로 이어붙인 새로운 배열을 생성한다.

#### 사용법 
```js
const newArr = arr.flat([depth]);
// depth: 중첩배열구조를 평탄화할 때 사용할 깊이 값. 기본값은 1
// 반환값: 하위 배열을 이어붙인 새로운 배열
```
```js
// 중첩배열 평탄화
const arr1 = [1, 2, [3, 4]];
arr1.flat();
// [1, 2, 3, 4]

const arr2 = [1, 2, [3, 4, [5, 6]]];
arr2.flat();
// [1, 2, 3, 4, [5, 6]]

const arr3 = [1, 2, [3, 4, [5, 6]]];
arr3.flat(2);
// [1, 2, 3, 4, 5, 6]

const arr4 = [1, 2, [3, 4, [5, 6, [7, 8, [9, 10]]]]];
arr4.flat(Infinity);
// 배열 구멍 제거
const arr5 = [1, 2, , 4, 5];
arr5.flat();
// [1, 2, 4, 5]

```
### forEach
> 주어진 함수를 배열 요소 각각에 대해 실행한다.
#### 사용법
```js
arr.forEach(callback(currentvalue[, index[, array]])[, thisArg])
// currentValue: 처리할 현재 요소
// index: 처리할 현재 요소의 인덱스
// array: forEach()를 호출한 배열
// thisArg: callback을 실행할 때 this로 사용할 값
```
```js
const array1 = ['a', 'b', 'c'];

array1.forEach((element) => console.log(element));
// "a"
// "b"
// "c"
```
### from
> 유사배열, 반복가능 객체를 얕게 복사해서 새로운 객체를 반환한다.
```js
console.log(Array.from('foo'));
// output: Array ["f", "o", "o"]

console.log(Array.from([1, 2, 3], (x) => x + x));
//  output: [2, 4, 6]

```