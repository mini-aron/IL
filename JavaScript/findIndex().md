# findIndex()
조건에 만족하는 배열의 `첫번째 요소의 인덱스`를 반환한다.  
만족하는 요소가 없으면 `-1`을 반환한다.

```js
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// Expected output: 3
```