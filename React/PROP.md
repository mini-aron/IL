## PROP
> prop(properties): 컴포넌트 속성을 설정할 때 사용하는 요소


### jsx 내부 props 렌더링

```
// MYcomponent.js
const MYComponent = prop =>{
  return <div>안녕하세요, 제이름은 {props.name}입니다.</div>
 };
 export defualt MYComponent;

// App.js
import MYComponent from './MYComponent';

const App =() => {
return <MYComponent name="React"/>
};

// result
안녕하세요, 제이름은 React입니다.
```

### props 기본값 설정:defaultProps
```
//App.js
import MYComponent from './MYComponent';

const App =() => {
return (
   <MYComponent/>
   <MYComponent name="React"/>
   )
};

// component.js
const MYComponent = prop =>{
  return <div>안녕하세요, 제이름은 {props.name}입니다.</div>
 };
 
 MYComponent.defaultProps ={
  name:'기본이름'
 };
 export defualt MYComponent;
 
 // result
안녕하세요, 제이름은 기본이름입니다.
안녕하세요, 제이름은 React입니다.
 
```
### children

```
//App.js
import MYComponent from './MYComponent';

const App =() => {
return (
   <MYComponent>REACT</MYComponent>
  
   )
};

// component.js
const MYComponent = prop =>{
  return (
    <div>
      안녕하세요, 제이름은 {props.name}입니다.<br/>
      children값은 {props.children}입니다.
    </div>
    )
 };
 
 MYComponent.defaultProps ={
  name:'기본이름'
 };
 export defualt MYComponent;
 
 // result
안녕하세요, 제이름은 기본이름입니다.
children값은 REACT입니다.
```

#### PropTypes 종류
+ array: 배열
+ arrayOf: 특정 PropType로 이루어진 배열
+ bool: true혹은false
+ func: 함수
+ number: 숫자
+ object: 객체
+ string: 문자열
+ symbol: ES6의 Symbol
+ node: 렌더링 할 수 있는 모든것( 숫자, 문자열, 혹은 jsx코드.)
+ instanceOf(클래스): 특정 클래스의 인스턴스(ex: instanceOf(MyClass))
+ oneOf(['dog','cat']): 주어진 배열 요소 중 값 하나
+ oneOfType([React.PropTypes.sring,PropTypes.number]): 주어진 배열 안의 종류중 하나
+ objectOf(React.PropTypes.number): 객체의 모든 키 값이 인자로 주어진PropType인 
