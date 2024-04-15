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
등록된 전역 상태를 사용하기 위해서는 `useRecoilState(키값)`를 사용하면 된다.
```js
function FontButton() {
  const [fontSize, setFontSize] = useRecoilState(State);
  return (
    <button onClick={() => setFontSize((size) => size + 1)} style={{fontSize}}>
      Click to Enlarge
    </button>
  );
```