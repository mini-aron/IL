## 배열 관련 메소드

### sort
> 배열을 오름차순 내림차순으로 정렬한다.
```js
let arr = [5, 3, 2, 4, 6, 1];
console.log(arr.sort()); //[1, 2, 3, 4, 5, 6]
console.log(arr.sort((a, b) => b - a)); //[6, 5, 4, 3, 2, 1]
```
