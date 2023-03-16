### react.memo
+ 고차 컴포넌트(Higher Order Component)이다.
+ ```props```가 이전과 동일한 값이면 재렌더링 하지 않고, 다른값이면 재렌더링하여 컴포넌트를 다시 만들어 반환한다.
+ ```React.memo```에 쓰인 컴포넌트 안에서 구현한```state```가 변경되면 컴포넌트는 재렌더링 된다.


### before use
```
import React,{useEffect,useMemo,useState} from 'react';
import Average from './Counter';


const TextView = ({ text }) => {
    useEffect(() =>{
        console.log('text 변경됨')
    });
    return <div>{text}</div>
}

const CountView = ({ count }) => {
    useEffect(()=>{
        console.log('count가 변경됨');
    });
    return <div>{count}</div>
}



function App() {
  const [count,setCount] = useState(0)
  const [text,setText] = useState("a")


  return (
    <div>
      <TextView text={text}/>
      <input value={text} onChange={(e)=> setText(e.target.value)}/>
      <br/>
      <CountView count={count}/>
      <button onClick={()=>setCount(count + 1)}>count 1 증가</button>
    </div>  
  );
}


export default App;

//input에 onChange이벤트가 실행 될때마다 count도 같이 리렌더링 된다..
```
### after use
```
import React,{useEffect,useMemo,useState} from 'react';
import Average from './Counter';


const TextView = React.memo(({ text }) => {
    useEffect(() =>{
        console.log('text 변경됨')
    });
    return <div>{text}</div>
})

const CountView = React.memo(({ count }) => {
    useEffect(()=>{
        console.log('count가 변경됨');
    });
    return <div>{count}</div>
})



function App() {
  const [count,setCount] = useState(0)
  const [text,setText] = useState("a")


  return (
    <div>
      <TextView text={text}/>
      <input value={text} onChange={(e)=> setText(e.target.value)}/>
      <br/>
      <CountView count={count}/>
      <button onClick={()=>setCount(count + 1)}>count 1 증가</button>
    </div>  
  );
}


export default App;
//memo가 prop에 대한 결과값을 기억해 prop값이 변하지 않으면 리렌더링 되지 않는다.
```
