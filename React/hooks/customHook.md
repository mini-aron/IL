## Custom Hook

- React에서 상태로직(stateful logic)을 재사용할 수 있도록 하는
- 기능이다.
  여러 컴포넌트에서 공통적으로 사용되는 상태로직을 추철해 하나의 함수로 만들어 사용할 수 있도록 한다.
- 커스텀 훅은 보통use라는 접두사를 사용하여 이름을 정의하며, React의 기본훅(useEffect,useState등)을 이용하여 구현된다.
- JSX코드나 렌더링과 관련된 코드를 포함해서는 안 되며, 컴포넌트 내부나 외부에서 호출해 사용한다.
- API 호출, 폼 데이터 관리, 타이머/애니메이션 등의 다양한 기능을 커스텀 훅으로 만들어 사용할 수 있다.

### 장점

- 코드의 중복을 줄인다.
- 컴포넌트의 재사용성과 유지보수성을 높일 수 있다.
- 
### Hook의 사용규칙
+ #### 최상위에서만 호출할 수 있다.
반목문, 조건문, 중첩된 함수 내에서 hook실행X
+ #### React 함수 컴포넌트 내에서만 Hook을 호출 해야한다.
일반 javascript함수에서 호출 X  
직접 작성한 custom hook 내 O
#### ex) 타이머를 사용하여 매초 구성요소의 상태를 업데이트하는 커스텀 훅

```js
import { useState, useEffect } from "react";

function useTimer(initialTime) {
  const [time, setTime] = useState(initialTime);

  useEffect(() => {
    const timer = setInterval(() => {
      setTime((prevTime) => prevTime + 1);
    }, 1000);

    return () => clearInterval(timer);
  }, [initialTime]);

  return time;
}
```
