## optional chaining
 optional chaining는 존재하지 않을 수 있는 값을 안전하게 호출 하기 위해 도와주는 문법이다.
   
 Optional chaining 연산자 ?.는 체인의 각 참조가 유효한지 명시적으로 검증하지 않고, 연결된 객체 체인 내에 깊숙이 위치한 속성 값을 읽을 수 있다.
 `?.`은 `?.`앞의 평가 대상이 undefined나 null이면 평가를 멈추고 undefined를 반환한다.
 ```js
console.log(data?.id) //값이 있다면 id를, 없으면 unndefined를 반환한다.
```
