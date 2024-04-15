## useEffect
useEffect는 컴포넌트들이 render와 paint된 후 실행된다.
비동기적으로 실행된다.
paint된 후 실행되기 때문에 useEffect 내부에 dom에 영향을 주는 코드가 있을경우 화면의 깜박임을 보게된다.

![[1_7jCVSsm5-gEoXsgmfGqQyw.webp]]

## useLayoutEffect
useLayoutEffect는 컴포넌트들이 render 된 후 실행되며 이후 paint가 된다. 
동기적으로 실행된다.
paint가 되기전 실행되기때문에 dom을 조작하더라도 사용자는 깜박임을 느낄 수 없다.
![[1_unEeZQLWQrxR93Ao8wBDDg.webp]]
### 결론
useLayoutEffect는 동기적으로 실행되고 내부의 코드가 전부 실행된후 painting작업을 하므로 로직이 복잡하면 레이아웃을 보기까지 시간이 오래걸린다.
이 떄문에 기본적으론 항상 useEffect만 사용하는걸 권장한다.
```tsx
cosnt Test (): JSX.Element => {
	const [value, setValue] = useState(0);
	useLayoutEffect(()=>{
		if(value === 0){
			setValue(10 + random() * 200);
		}
	},[value]);

	console.log('render',value);

	return(
		<button onClick={()=> setvalue(0)}>
			value: {value}
		</button>
	)
}
```
fetch, event handler, state reset등은 useEffect를 사용하되,
위 코드같이 state가 존재하며 해당 state에 따라 painting시 다르게 렌더 되어야할때는 useLayoutEffect를 사용하는 것이 좋다.