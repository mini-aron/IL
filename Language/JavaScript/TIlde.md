# tilde(~) & double tilde(~~)

## tilde(~)연산자
```js
let number = 5;// 0000000000000101
console.log(~number); // 1111111111111010
//output: -6
```

## double tilde(~~)
> tilde를 2번 반복한다.

### 장점
+ 1. Math.floor()대신 사용될 수 있다.
    - 숫자에 ~연산을 하게되면서 소수점들은 버려지게된다. 즉, ~~를 활용하면 Math.floor() 처럼 활용할 수 있다.
+ 2. undefined 또는 null을 0으로 변환할 때 사용될 수 있다.