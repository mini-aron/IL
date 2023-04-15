### poltmorphism(다형성)
```
type SuperPrint = {
   <T>(arr: T[]):T
}

const superPrint: SuperPrint = (arr) => {
  return arr[0]
}

superPrint([1, 2, 3, 4])
superPrint([true, false, true])
superPrint(["a", "b", "c"])
superPrint([1, 2, true, false])
```
+ typescript가 타입을추론함
