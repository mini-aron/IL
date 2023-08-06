## 배열 관련 메소드

### sort
> 배열을 오름차순 내림차순으로 정렬한다.
```js
let arr = [5, 3, 2, 4, 6, 1];
console.log(arr.sort()); //[1, 2, 3, 4, 5, 6]
console.log(arr.sort((a, b) => b - a)); //[6, 5, 4, 3, 2, 1]
```

### join
> 배열을 문자열로 변환한다.
```js
arr.join(); // 구분자를 넣지 않으면 컴마가 포함되어 문자열로 합쳐진다.
arr.join('.');  // 구분자를 넣어주면 아이템 사이에 구분자를 넣어서 문장여로 합쳐진다.
```

```js
let arr = ['apple', 'banana', 'orange'];
console.log(arr.join()); // 'apple,banana,orange'
console.log(arr.join(' ')); //'apple banana orange'
```
### split
> 문자열을 배열로 변환한다.

```js
let arr = 'A,B,C,D';
console.log(arr.split(','));  //[A, B, C, D];
```
### reverse
> 배열의 아이템의 순서를 뒤집는다.

```js
let arr = [1, 2, 3, 4, 5, 6];

console.log(arr.reverse()); //[6, 5, 4, 3, 2, 1]
console.log(arr);  // [6, 5, 4, 3, 2, 1] 원래배열도 변경되어있다.
```