# sort
 
## 구문
```js
arr.sort((a,b) => {return a - b})
```


## 예제
```js
var numbers = [4, 2, 5, 1, 3];
numbers.sort(function(a, b) {
  return a - b;
});
console.log(numbers);

// [1, 2, 3, 4, 5]
```