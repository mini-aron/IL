

# map() 메서드
+ map()메서드는 배열을 순회하며 주어진 함수의 결과를 모아 새로운 배열을 리턴한다.
```
let array = [1,2,3]
let newArray = array.map((num,index,arr)=>{console.log(num,index,arr)})

//result
1 0 [1,2,3]
2 1 [1,2,3]
3 2 [1,2,3]

```
## ex
```
let numbers = [1, 4, 9]

let square = numbers.map(function(num) {
    return num*num
})

//result
[1,16,81]
```
