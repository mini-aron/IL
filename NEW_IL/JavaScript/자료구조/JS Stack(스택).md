선형 데이터 구조의 자료구조이다.
가장 최근 요소부터 처리하는 LIFO 메커니즘을 가지고있다.

장점
+ 동적인 메모리 사이즈
+ 빠른 런타임
+ 데이터의 삽입 순서대로 정렬

단점
+ 가장 최신요소만을 가져옴
+ 한번에 하나의 데이터만 처리 가능

사용
+ 가장 마지막에 입력된 것을 순차적으로 처리하고싶을 때
+ 브라우저의 뒤로가기
+ 실행 취소
+ 재귀

### JS에서 배열로 stack만들기
```js


class stack(){
    constructor(){
        this.items = [];
    }

    push(item) {
        this.items[this.items.length] = item;
    }

    pop(){
        this.items.length = this.items.length -1
    }

    peek(){
        if(this.items.length===0){
            return null;
        }
        return this.items[this.items.length];
    }

    getSize(){
      return this.items.length;  
    }

    isEmpty(){
        return getSize()===0;
    }
}
```