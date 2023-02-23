## reduce
+ reduce()메서드는 각 요소에 대해 reducer합수를 실행하고, 하나의 결과값을 반환함
### basic
```
Array.reduce( callBackFunction( accumulator, cuurentValue, currentIndex, source ),initialValue )
```
+ accumulator: 콜백의 반환값을 누적(initialValue를 제공한 경우에는 initialValue의 값)
+ cuurentValue: 처리할 현재 요소
+ currentIndex(optional): 처리할 현재 요소의 인덱스(initialValue를 제공한 경우 0, 아니면 1부터 시작)
+ array (Optional): reduce()를 호출한 배열
+ initialValue (Optional): callback의 최초 호출에서 첫 번째 인수에 제공하는 값(초기값을 제공하지 않으면 배열의 첫번째 요소를 사용)<br/>
=> 빈 배열에서 초기값 없이 reduce를 호출하면 오류 발생
### ex
```
const array = [1,2,3,4,5]

const add = array.reduce(function(acc,value){
  return acc+value;
} )
console.log(add);

//output
15
```
```
//use initialValue

array.reduce(function(acc,value){
  return acc+value;
},0 or [] or '')
```
