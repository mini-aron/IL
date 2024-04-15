# findIndex()
조건에 만족하는 배열의 `첫번째 요소의 인덱스`를 반환한다.  
만족하는 요소가 없으면 `-1`을 반환한다.

```js
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// Expected output: 3
```

## 사용법
```js
arr.findIndex(callback(element[,index[,array]])[, thisArg])
```
#### 매개변수
 `callback`  
 3개의 인수를 취해 배열의 각 값에 대해 실행할 함수  
 `element`  
 배열에서 처리중인 현재 요소  
 `index`  
 배열에서 처리중인 현재 요소의 인덱스  
 `array`  
 findIndex함수가 호출된 배열  
 `thisArg`  
 선택사항, 콜백을 실행할 때 this로 사용할 객체