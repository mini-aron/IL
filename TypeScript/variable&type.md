## variable

```
let a : number = 1;
let b : string = "i1";
let c : boolean = true

let a : number[] = [1,2];
let b : string[] = ["i1","1];
let c : boolean[] = [true]


```


```
type Age = number;
type Name = string;
type Player = {
    readonly name:Name
    age?:Age
}

const playerMaker = (name:string) : Player => ({name})
const nico = playerMaker("nico")
nico.age = 12 
```
type age?: number (number | undefined)
+ readonly: 읽기전용 

```
const numbers: readonly number[] = [1, 2, 3, 4]
numbers.push(1)//err

const names: readonly string []= ["1","2"]

const player: readonly[string, number, boolean] = ["nico", 1, true]
```
### any
```
let a = [] //let a: any[]


const a: any[] = [1, 2, 3, 4]
const b : any = true

a + b // not problem
```
+ any: 모든 타입(타임스크입트를 빠져나오는 방법)

### unknown
```
let c: unknown;

let d = a + 1 //err

if(typeof c === 'number'){
    let e = c + 1
}
if(typeof c === 'string'){
    let e = c.toUpperCase()
}

```
+ unknown: 타입을 미리 알지 못할 때 사용(여러 case에 대해 만들 수 있음)

### void
```
function hello(){
    console.log('x')
}
```
+ void: 아무것도 return하지 않는 function

### naver
```
function hello(name:string|number){
    if(typeof name === "string"){
        name //type string
    }else if (typeof name === "number"){
        name //type number
    }else{
        name //type never
    }
}
```
