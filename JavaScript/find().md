# find()
조건을 만족하는 `첫번째 요소`의 값을 반환한다.  
만약 조건을 만족하는 요소가 없다면 undefined를 반환한다.

```js
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// Expected output: 12

```
