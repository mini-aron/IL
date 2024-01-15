## useState?
useState는 react의 기본제공 hook 중 하나로, 상태 변수를 추가할 수 있게 해주는 함수다.
2개의 원소 배열을 반환하며, 첫번째 원소는 상태값, 두번째 원소는 상태 값을 변경하기 위한 setter 함수가 반환된다.
보통 아래의 구조와 같이 선언하여 사용한다.
```js
const [ state, setState ] = useState(initialState);
```

### 상태값 변경시 리렌더링 발생
useState에서 반환된 배열의 두번째 값인 setter함수를 호출하게 되면 상태 값을 변경할 수 있고, 리렌더링이 진행된다.

### 상태값 변경은 비동기적으로 동작
useState의 setter 함수를 호출한 이후 바로 다음줄에서 해당 state값을 참조하게되면 바뀌기 이전 state가 참조된다. 
이유는 useState의 setter함수가 비동기적으로 동작하기 때문이다. 
setter함수의 인자에 새로운 값이나 함수를 전달하게 되면 바로 상태가 업데이트 되는게 아니라 그 값이나 함수는 대기열에 들어가게 된다. 그리고 리렌더링이 진행될때 대기열에 들어가 있던 값으로 상태가 업데이트 되거나 함수가 호출되어 상태가 업데이트된다.

### 업데이터 함수로 상태를 변경해야 하는 이유
setter 함수의 인자에 값을 넣을 수도 있지만 함수를 넣을 수도 있다.
 이전 상태를 기반으로 상태를 업데이트 하기 위해서는 업데이터 함수를 사용해 값을 변경해야한다.
업데이터 함수는 인자에 prop으로 현재 값이 넘어오기때문에 이전값을 참조하며 업데이트가 가능하다.
```js
const [number, setNumber] = useState(0);

useEffect(() => {
	setNumber(number + 1); //0 + 1
	setNumber(number + 1); //0 + 1
	setNumber(number + 1); //0 + 1
	setNumber(number + 1); //0 + 1
	setNumber(number + 1); //0 + 1
}, []);
```

```js
const [number, setNumber] = useState(0);

useEffect(() => {
	setNumber(prev => prev + 1); //0 + 1
	setNumber(prev => prev + 1); //1 + 1
	setNumber(prev => prev + 1); //2 + 1
	setNumber(prev => prev + 1); //3 + 1
	setNumber(prev => prev + 1); //4 + 1
}, []);
```

### 짧은 시간안에 setter 함수를 연속적으로 호출 시 렌더링은 1번만 진행된다.
```js
"use client" 
import { useEffect, useState } from "react";
export default function Page() { 
	const [number, setNumber] = useState(0); 
	useEffect(() => { 
		setNumber(prev => prev + 1); 
		setNumber(prev => prev + 1); 
		setNumber(prev => prev + 1); 
		setNumber(prev => prev + 1); 
		setNumber(prev => prev + 1); 
	}, []); 
	
	useEffect(() => { 
		console.log(`[${performance.now()}] 렌더링 완료됨. number => ${number}`);
	}, [number]); 
	return ( 
	<> 
		{ 
			(function() { 
				console.log(`[${performance.now()}] component return 됨.`); 
				return <></>; 
		}
		<div className="w-full relative">
			 현재 number 값 : { number } 
		</div> 
	</> 
	); 
 }
```
리액트에서는 배치 상태 업데이트라고 하여 짧은 시간 이내에 setter 함수가 연속적으로 호출 되었을 경우에는 호출 된 값 또는 업데이터 함수들을 큐에 집어 넣어 놓고 대기한다.
그리고 짧은 시간이 지난 후 큐에 집어 넣은 것들을 순차적으로 일괄호출하기 시작한다.
이런 배치 상태 업데이트 방식을 채택하고있어 setter 함수를 연속으로 호출해도 렌더링은 1번만 발생시키는 것이 가능하다. 