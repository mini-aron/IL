### JSX
+ JSX는 자바스크립트 형태의 확장 문법
+ 코드가 번들링 되는 과정에서 바벨을 사용하여 자바스크립트의 형태로 변환

### Jsx 변환과정
```
funtion App() {
  return(
  <div>
    Hello<b>react</b>
  </div>
  );
}
```
↓↓↓↓↓↓
```
function App() {
  return React.createElement("div",null,"hello",React.createElement("b",null,"react"));
}
```





















