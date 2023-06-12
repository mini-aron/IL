# filter() 매서드
+ filter()매서드는 배열을 순회하며 요소마다 조건 확인 후 조건에 만족하는 원소로 구성된 새 배열을 리턴한다.
```
let array = [1,2,3]
let newArray = array.filter((num,index,arr)=>{console.log(num,index,arr)})

//result
1 0 [1,2,3]
2 1 [1,2,3]
3 2 [1,2,3]

```
## ex
```
const words = ['react','javascript','parameter','argument']
const result = words.filter(word => word.length > 6);
console.log(result);

//output
['javascript','parameter','argument']
```
