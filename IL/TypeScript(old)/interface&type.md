## interfaces
```ts
type Team = "red" | "blue" | "yellow"
type Health = 1 | 5 | 10


interface Player  {
    nickname: string,
    team:Team
    health:Health
}

const nico : Player = {
    nickname:"nico",
    team:"red",
    health: 10
}
```
+ interface:모양,틀 type과 같게 쓰이지만 약간의 차이가 있음. type이 더 많이쓰임
+ 객체에만 사용 가능함

### interface 사용
```ts
interface User {
    name:string
}

interface Player extends User{   
}
const nico : Player = {
    name: "nico"
}

```
### type 사용
```ts


type User = {
    name: string
}

type Player = User & {

}

const nico : Player = {
    name: "nico"
}
```

### interface의활용

+ typescript
```ts

interface User {
    
    firstName:string,
    lastName:string,
    sayHi(name:string):string
    fullName():string
}

interface Human {
    health:number,
}

class Player implements User, Human{
   constructor(
    public firstName:string,
    public lastName:string,
    public health:number
   ){}
   fullName(){
    return `${this.firstName} ${this.lastName}`
   }
   sayHi(name:string){
    return `hello ${name}. My name is ${this.fullName}`
   }
}

function makeUser(user:User){
    return "hi"
}

makeUser({
    firstName:"nico",
    lastName:"las",
    fullName: () => "xx",
    sayHi: (name) => "string"
})
```
+ javascript
``` ts
"use strict";
class Player {
    constructor(firstName, lastName, health) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.health = health;
    }
    fullName() {
        return `${this.firstName} ${this.lastName}`;
    }
    sayHi(name) {
        return `hello ${name}. My name is ${this.fullName}`;
    }
}
function makeUser(user) {
    return "hi";
}
makeUser({
    firstName: "nico",
    lastName: "las",
    fullName: () => "xx",
    sayHi: (name) => "string"
});
```

