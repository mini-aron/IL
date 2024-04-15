# every()
> .every()는 배열의 모든 원소가 조건에 맞는지 검사하는 메서드이다.
> 모든 원소가 조건을 만족하면 true, 하나라도 만족하지 않으면 false를 반환한다.

# some()
> .some()은 마찬가지로 배열의 원소가 조건에 맞는지 검사하는 메서드이다.
> every()와 다른점은 배열의 요소 1개라도 조건을 충족하면 true를 반환한다.
```js
const array = [1, 2, 3, 4];
let result = array.every(num => num > 2);
console.log(result); //false
result = array.some(num => num > 2);
console.log(result); //true
```
## 문법
```js
// 화살표 함수
every((element) => { ... } )
every((element, index) => { ... } )
every((element, index, array) => { ... } )

// 콜백 함수
every(callbackFn)
every(callbackFn, thisArg)

// 인라인 콜백 함수
every(function callbackFn(element) { ... })
every(function callbackFn(element, index) { ... })
every(function callbackFn(element, index, array){ ... })
every(function callbackFn(element, index, array) { ... }, thisArg)
```
+ callbackFn : 각 요소를 시험할 함수. 다음 세 가지 인수를 받는다.
  - element : 배열에서 처리되는 현재 요소
  - index : 처리할 현재 요소의 인덱스
  - array : every를 호출한 배열
  - thisArg(optional) : callbackFn을 실행할 때 thi값
