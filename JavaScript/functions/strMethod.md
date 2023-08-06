# 문자열 메소드들

### length
> 문자열 길이 반환
```js
let text = "Hello, Javascript!";
console.log(text.length); // 18
```
### slice, substring, substr
+ #### slice, substring(start_index, end_index)
  > 두 메소드의 사용방법은 동일하고 시작인덱스부터 끝인덱스-1까지 출력한다.
  > 전달한 값이 음수라면 인덱스를 뒤에서부터 계산한다.
+ #### substr(start_index,n)
  >시작인덱스부터 n의 길이만큼 출력한다.
```js
// idx 2부터 끝까지 출력
console.log('slice: ', text.slice(2));

// idx 3부터 ~ idx 9전 까지 (3~8) 출력
console.log('slice: ' , text.slice(3,9));
console.log('substring :', text.substring(3,9));

// idx 3부터 총 9글자 될 때까지 출력
console.log('substr :', text.substr(3,9));

// idx 2부터 뒤에서부터 3번째까지 출력
console.log('slice: ', text.slice(2, -3)); 
```
### toUpperCase, toLowerCase
> 대/소문자로 치환시킨다.
```js
let text = "Hello, Javascript!";
console.log('toUpperCase: ', text.toUpperCase());  // HELLO, JAVASCRIPT!
console.log('toLowerCase: ', text.toLowerCase());  // hello, javascript!
```
### trim
> 공백제거
```js
console.log('after trim: ','      ABCDEFG'.trim()); //ABCDEFG
```

### padStart().padEnd()
+ #### padStart(n,string)
  > 문자의 총킬이를 n만큼, 모자란 공간은 문자열의 앞에 string으로 채운다.
+ ### padEnd(n,string)
  > 문자의 총길이를 n만큼, 모자란 공간은 문자열의 뒤에 string으로 채운다.
```js
console.log('after padding:', 'ABCDEF'.padStart(13,'#').padEnd(20,'*')); //#######ABCDEF*******
```

### chatAt()
+ #### text.chatAt(n),text[n]
  > 문자열의 n번째 idx에 해당하는 문자를 반환
+ #### text.charCodeAt(n)
  > 문자열의 n번째 idx에 해당하는 문자의 코드 반환
```js
console.log('ABCDEF'.charAt(3));         // D
console.log('ABCDEF'[3]);                // D
console.log('ABCDEF'.charCodeAt(3));     // 68
```
### split()
> 문자열을 원하는 기준으로 잘라 반환
```js
fruits = "apple/banana/lemon"

const fruit_arr = fruits.split('/');
console.log('fruit_arr ', fruit_arr); //[apple, banana, lemon]
```

### indexOf()
> indexOf()는 처음부터 찾고 lastIndexOf는 끝에서부터 찾는다.
> 만약 일치하는 결과가 없을경우 -1을 반환한다.
```js
var text = "Hello, Javascript!  Hello, Javascript!";

console.log(text.indexOf('a'));        // 8
console.log(text.indexOf('b'));        // -1  (못찾은 경우)
console.log(text.indexOf('Java', 10)); // 27  (10 부터 찾는다)

console.log(text.lastIndexOf('a'));    // 30  (뒤에서부터 찾는다)
console.log(text.lastIndexOf('a',20)); // 뒤에서부터 idx 20 까지 찾는다.
```

### includes()
> 해당 문자열이 포함된 여부를 반환한다 
```js
var names= "홍길동,박길동,남궁민수,김철수";

console.log(names.includes('홍길동'));  // true
console.log(names.includes('김길동'));  // false
```
### startsWith(), endsWith()
> 해당문자열로 시작했는지 여부를 반환한다.
```js
var text = "Hello, Javascript!  Hello, Javascript!";

console.log(text.startsWith("hello"));  // false
console.log(text.startsWith("Hello"));  // true

console.log(text.endsWith("script!"))  // true
```
