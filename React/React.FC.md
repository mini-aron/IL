# React.FC
Function Component 타입의 줄임말로, react + Typescript 조합으로 개발할 때 사용하는 타입이다.  
함수형 컴포넌트(화살표 함수) 사용시 타입선언에 쓸 수 있도록 React에서 제공하는 타입이다.  
## React.FC 사용
```js
import React from 'react';
type GreetingsProps = {
  name: string;
};
const Greetings: React.FC<GreetingsProps> = ({ name }) => (
  <div>Hello, {name}</div>
);
export default Greetings;
```
React.FC를 사용하는 경우에는 다음과 같이 props의 타입을 Generics으로 넣어서 사용한다.

## React.FC의 단점
### 1. optional children
```js
export const Hello: React.FC<HelloProps> = ({ name }) => {
  return <h1>Hello olleh! my name is {name}</h1>
}

const App = () => (
  <>
    <Hello name="suzi">
      <span>{"I have children"}</span>
    </Hello>
  </>
)
```
위 코드를 보면 Hello 컴포넌트는 children을 렌더링하는 부분이 없음에도 불구하고 App 컴포넌트에서 오류 없이 정상적으로 작동한다.  
  
이는 타입스크립트를 사용하면서 충분히 혼란을 줄 수 있는 여지가 있다.  
  
컴포넌트에 children의 존재가 가능한지 여부를 확인하는 방법이 좋다.
만약 컴포넌트에 children이 존재할 수 도 있다는 것을 알려주기 위해서는
PropsWithChildren을 사용하는 것이 좋다. 아래와 같이 사용하면 된다.
```js
function Card({ title, children }: PropsWithChildren<{ title: string }>) {
  return (
    <>
      <h1>{title}</h1>
      {children}
    </>
  )
}
```
### 2. defaultProps
React.FC 에서는 defaultProps를 사용하지 못하게 한다.

```js
export const Hello: React.FC<HelloProps> = ({ name }) => {
  return <h1>Hello olleh! my name is {name}</h1>
}

Hello.defaultProps = {
  name:"aron"
}

const App = () => (
  <>
    <Hello />
  </>
)
```
위의 코드를 실행하면 name에 aron가 들어오지 않는다.