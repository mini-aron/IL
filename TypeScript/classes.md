## classes
```

abstract class User {
    constructor(
        protected firstName:string,
        protected lastName:string,
        protected nickname:string,
    ){}
    abstract getNickName():void
    getFullName(){
        return `${this.firstName} ${this.lastName}`
    }
}

class Player extends User{
    getNickName(){
        console.log(this.nickname)
    }
}

const nico = new Player("nico","las","니코");


```
private:상속은 가능하나 접근이 안됨
protected:상속으로 접근가능,외부클래스에서 접근 

```
type Words  ={
    [key:string] :string
}


class Dict {
   private words:Words
   constructor(){
    this.words = {}
   }
   add(word:Word){
        if(this.words[word.term]=== undefined){
            this.words[word.term] = word.def
        }
   }
   def(term:string){
    return this.words[term]
   }
}

class Word {
    constructor(
        public term:string,
        public def:string,
    ){}
}

const kimchi = new Word("kimchi","한국음식")

const dict = new Dict()

dict.add(kimchi)
dict.def("kimchi")

```
class를 type처럼 씀
추상클래스 잘보기
