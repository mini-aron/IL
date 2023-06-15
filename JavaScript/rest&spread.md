# rest와 spread의 차이

## rest 
+ 함수의 매개변수에 점(...)을 사용해 표현한다.
+ rest매개변수는 모든 요소를 배열로 모은것으로 여러 개의 함수 인수를 전달할 경우 사용된다.

```js
function printNumber(one,two,...rest) {
    console.log(one);
    console.log(two);
    console.log(rest);
}
printNumber(1, 2, 3, 4, 5, 6, 7);
```
```
실행결과
1
2
[3, 4, 5, 6, 7]
```

```js
let arrNumber = [1, 2, 3, 4, 5];
let [firstNumber, ...restNumber] = arrNumber;

console.log(firstNumber);
console.log(restNumber);
```
```
실행결과
1
[2, 3, 4, 5]
```
## spread
+ 함수 호출에 점(...)을 사용해 표현한다.
+ spread연산자는 압축되어 있는 값을 단일요소로 푸는 기능을 수행한다.
```js
function sumFunc(firstParam, secondParam) {
  return firstParam + secondParam;
}

let arrNumber = [10, 20];
let sumValue = sumFunc(...arrNumber);

console.log(sumValue); 
```
```
실행결과
30
```
```js
let arrNumber = [1, 2, 3];

// 배열 복사
let copyArrNumber = [...arrNumber];

// 배열에 값 추가
let addArrNumber = [...arrNumber, 4, 5, 6];

console.log(copyArrNumber);
console.log(addArrNumber);
```
```
실행결과
[1, 2, 3]
[1, 2, 3, 4, 5, 6]
```