## JS로 queue를 짜보자!!
```js
calss Queue {
    constructor(){
        this.storage = {};
        this.front = {};
        this.rear = 0;
    }
       // 크기구하기
    size (){
        if(this.storage[this.rear] === undefined) {
            return 0;
        }else{
            return this.rear - this.front + 1;
        }
    }

    add(value) {
        if(this.size() === 0) {
            this.storage['0'] = value;
        } else {
            this.rear += 1;
            this.storage[this.rear] = value;
        }
    }

    popleft() {
        let temp; 
        if(this.front === this.rear) {
            temp = this.storage[this.front];
            delete this.storage[this.front];
            this.front +=1;
        }
        return temp;
    }
}
```