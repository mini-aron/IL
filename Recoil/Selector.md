# Selector

selector는 전역 상태를 기반으로 어떤 계산을 통해 새로운 값을 내뱉는 순수함수다.  
atom이나 다른 selector을 통해 입력받을수 있다.  

상위의atom이나 다른selector가 업데이트 되면 하위 selector 함수도 다시 실행된다.  
컴포넌트들은 atom을 사용했던 것처럼 selector를 사용할 수 있다.  
  
최소한의 기본적인 상태들은 atom에 저장하고, seletor에 명시한 함수를 통해 상태값을 변경하면 된다.  
  
컴포넌트의 관점으로 봤을 때 atom과 seletor은 동일한 인터페이스를 가지므로 대체해 사용할 수 있는 것이다.  

```js
const fontSizeLabelState = selector({
  key: 'fontSizeLabelState', // 고유한 키 값
  get: ({get}) => {
    const fontSize = get(fontSizeState); 
    const unit = 'px';

    return `${fontSize}${unit}`;
  },
});
```
+ get은 생태를 계산할 함수가 담겨져 있다.   
get으로 전달되는 매개변수를 통해 atom이나 다른seletor에 접근할 수 있다.  
  
위 예시에서 selector는 fontSizeState라는 atom에 의존성을 갖는다.  
```js
function FontButton() {
  const [fontSize, setFontSize] = useRecoilState(fontSizeState);
  const fontSizeLabel = useRecoilValue(fontSizeLabelState);

  return (
    <>
      <div>Current font size: ${fontSizeLabel}</div>

      <button onClick={setFontSize(fontSize + 1)} style={{fontSize}}>
        Click to Enlarge
      </button>
    </>
  );
}
```
selector는 `useRecoilValue(키값)`을 통해 사용할 수 있다.
버튼을 클릭하면 폰트 사이즈도 증가하는 동시에 `fontSizeLabel`도 업데이트 되어 컴포넌트에 반영된다.

