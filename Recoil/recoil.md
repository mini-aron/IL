# Recoil
Rcoil은 페이스북이 2020년에 소개한 React전용 상태 관리 라이브러리다.  
  
contextAPI는 상태를 전달할 때 객체형태의 value를 사용한다. 
따라서 객체 안의 값이 하나라도 변경되면 provider로 감싼 모든 하위 컴포넌트가 리렌더링 된다는 단점이 있다.  
하진만 Recoli의 경우 각각 전역 상태에 대한 atom이 생성되고 해당 상태를 구독하는 구성요소만 리렌더링 된다.  
이로써 불필요한 리렌더링을 방지할 수 있다.

## 주요개념
### data-flow graph
상태 데이터가 atoms -> selectors -> 컴포넌트 순서로 흐르는 것을 말한다.
### Atoms
Atoms는 상태 단위이며, 업데이트와 참조가 가능하다.
atom이 업데이트되면 각각의 컴포넌트들은 새로운 값을 반영하여 리렌더링 된다.
atoms는 컴포넌트 내부의 상태 대신 사용될 수 있다.
동일한 atom이 여러 컴포넌트에서 사용되는 경우 그 컴포넌트들은 상태를 공유한다.

Atoms는 atom 함수를 사용해 생성한다.
atom의 키 값은 전역적으로 고유해야 한다.
```js
const fontSizeState = atom({
  key: 'State', // 고유한 키 값
  default: 14,
});
```
등록된 전역 상태를 사용하기 위해서는 useRecoilState(키값)를 사용하면 된다.
```js
function FontButton() {
  const [fontSize, setFontSize] = useRecoilState(State);
  return (
    <button onClick={() => setFontSize((size) => size + 1)} style={{fontSize}}>
      Click to Enlarge
    </button>
  );
```