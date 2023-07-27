# forEach
배열 요소 각각에 대해 함수를 실행한다

## 사용법
```js
    arr.forEach(callback(currentvalue[, index[, array]])[, thisArg])
```
+ callback  
  각 요소에 대해 실행할 함수. 다음 세 가지 매개변수를 받습니다.  

+ currentValue  
  처리할 현재 요소.  

+ index  
  처리할 현재 요소의 인덱스.<  

+ array  
  forEach()를 호출한 배열.  

+ thisArg
  callback을 실행할 때 this로 사용할 값.  

## ex
```js
const array1 = ['a', 'b', 'c'];

array1.forEach(element => console.log(element));

// Expected output: "a"
// Expected output: "b"
// Expected output: "c"
```