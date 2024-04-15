## Math 메소드 총정리
> math 객체는 수학 상수와 함수를 위한 프로퍼티와 메소드를 제공하는 빌트인 객체이다.  
math 객체는 생성자 함수가 아니다.  
따라서 Math객체는 정적 프로퍼티와 메소드만 제공한다.

### Math.abs(number) : number
> 절대값 반환
```js
Math.abs(-1);       // 1
Math.abs('-1');     // 1
Math.abs('');       // 0
Math.abs([]);       // 0
Math.abs(null);     // 0
Math.abs(undefined);// NaN
```

### Math.round(number) : number
> 소수점 이하를 반올림한 정수를 반환
```js
Math.round(1.4);  // 1
Math.round(1.6);  // 2
Math.round(-1.4); // -1
Math.round(-1.6); // -2
Math.round(1);    // 1
Math.round();     // NaN
```

### Math.ceil(number) : number
> 소수점 이하를 올림한 정수를 반환
```js
Math.ceil(1.4);  // 2
Math.ceil(1.6);  // 2
Math.ceil(-1.4); // -1
Math.ceil(-1.6); // -1
Math.ceil(1);    // 1
Math.ceil();     // NaN
```

### Math.floor(number) : number
> 소수점 이하를 내림한 정수를 반환 - Math.ceil의 반대개념

```js
Math.floor(1.9);  // 1
Math.floor(9.1);  // 9
Math.floor(-1.9); // -2
Math.floor(-9.1); // -10
Math.floor(1);    // 1
Math.floor();     // NaN
```

### Math.sqrt(number) : number
> 제곱근을 반환
```js
Math.sqrt(9);  // 3
Math.sqrt(-9); // NaN
Math.sqrt(2);  // 1.414213562373095
Math.sqrt(1);  // 1
Math.sqrt(0);  // 0
Math.sqrt();   // NaN
```

### Math.random() : number
> 임의의 부동 소수점을 반환  
반환된 부동소수점은 0부터 1이하  
```js
Math.random(); // 0 ~ 1 미만의 부동 소수점 (0.8208720231391746)

/*
1 ~ 10의 랜덤 정수 취득
  1) Math.random로 0 ~ 1 미만의 부동 소수점을 구한 다음, 10을 곱해 0 ~ 10 미만의 부동 소수점을 구한다.
  2) 0 ~ 10 미만의 부동 소수점에 1을 더해 1 ~ 10까지의 부동 소수점을 구한다.
  3) Math.floor으로 1 ~ 10까지의 부동 소수점의 소수점 이하를 떼어 버린 다음 정수를 반환한다.
*/
const random = Math.floor((Math.random() * 10) + 1);
console.log(random); // 1 ~ 10까지의 정수
```

### Math.max(...number) : number
> 인수중 가장 큰 수를 반환

```js
Math.max(1, 2, 3); // 3

const arr = [1, 2, 3];
const max = Math.max.apply(null, arr) //3
Math.max(...arr); // 3
```

### Math.min(...number) : number
> 인수중 가잩 작은 수를 반환
```js
Math.min(1, 2, 3); // 1
Math.min(...arr); // 1
```