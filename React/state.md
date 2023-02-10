### state
+ 컴포넌트 내부에서 바뀔 수 있는 값

#### 클래스 컴포넌트의 state 

Counter.js

```
 import { Component } from 'react';
 
 class Counter extends Component {
  constructor(prop) {
    super(props);
    //state의 초기값 설정
    this.state= {
      number: 0
    };
  }
  render(){
    const {number} = this.state; //state를 조회할 때는 this.state로 조회
    return (
      <div>
        <h1>{number}</h1>
        <button
          onClick={()=>{
           this.state({ number: number+1 });
          
          }}
        >
        +1
        </button>
      </div>
    )
  }
 }
```
