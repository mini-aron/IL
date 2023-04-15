### call signature
```
type Add = (a:number, b:number) => number

const add: Add = (a, b) => a + b

```
### overloading
```
type Add = {
    (a: number, b: number) : number
    (a: number, b: string) : number
}

const add: Add = (a, b) => {
    if (typeof b === "string") return a
    return a + b
}


```
+ overloading: 여러 call signatures가 있는 함수
### ex)
```
type Config = {
    path: string,
    state: object
}

type Push = {
    (path:string):void
    (config:Config): void
}

const push:Push = (config) => {
    if(typeof config === "string"){
        console.log(config)
    }else{
        console.log(config.path,config.state)
    }
}
```
```
type Add = {    //다른 call signatures에 파라미터의 개수가 다른 예
    (a: number, b: number):number
    (a: number, b: number, c: number): number,
}
                           //선택사항이라는것을 알려주기위한 파라미터
const add:Add = (a, b, c?:number) => {
    if(c) return a+ b + c
    return a + b
}
add(1, 2)
add(1, 2, 3)
```
