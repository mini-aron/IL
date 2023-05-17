# enum, const enum, as const의 차이

## enum 
+ 열거형 타입
+ 대표적인 예로 boolen Type을 생각할 수 있다.
+ 일반적으로 JS에서 숫자 1은 Ture,0은 False에 대응되는데 , 일종의 Built-in enum인 셈이다.
```js
enum booleanType {
  False = 0,
  True = 1
}
↓↓↓↓ -- JS 컴파일

"use strict";
var booleanType;
(function (booleanType) {
  booleanType[booleanType["false"] = 0] = "False";
  booleanType[booleanType["True"] = 1] = "True";
})( booleanType || (booleanType = {}));
// 아래코드와 같은 객체를 반환하는 즉시실행 함수를 구현했을 뿐이다.

var booleanType = {
  "0":"False",
  "1":"True",
  "False":0,
  "True":1
}
```
