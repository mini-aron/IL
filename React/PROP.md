## PROP
> prop(properties): 컴포넌트 속성을 설정할 때 사용하는 요소


### jsx 내부 props 렌더링
#### component.js
```
const MYComponent = prop =>{
  return <div>안녕하세요, 제이름은 {props.name}입니다.</div>
 };
 export defualt MYComponent;
```
#### App.js
```
import MYComponent from './MYComponent';

const App =() => {
return <MYComponent name="React"/>
};
```
#### result
```
안녕하세요, 제이름은 React입니다.
```

