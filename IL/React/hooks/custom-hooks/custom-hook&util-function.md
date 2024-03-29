## util function과 custom hook의 차이점

#### 날짜문자열을 특정형식으로 지정하는 유틸함수

```js
function formatData(dateString, format) {
  const date = new Date(dateString);
  return date.toLocaleDateString(format);
}
```

#### 타이머를 사용하여 매초 구성요소의 상태를 업데이트하는 커스텀 훅

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

#### 기능구성요소에서의 사용

```js
function Timer() {
  const time = useTimer(0);

  return <div>{time}</div>;
}
```

- 유틸함수 : 특정작업을 수행하고 애플리케이션의 여러 부분에서 재사용 가능한 독립 실행형 함수다. 일반적으로 입력 인수를 받아 계산을 수행하고 결과를 반환한다.
- 커스텀 훅 : React hook을 사용하여 구성요소에 특정 동작이나 기능을 제공하는 기능이다. 재사용이 가능하도록 설계되어 기능구성요소 내에서 호출할 수 있다.

> 유틸함수는 어느곳에서나 사용할 수 있는 독릭 실행형 합수인 반면 커스텀 훅은 React hooks를 사용해 구성요소에 특정 동작이나 기능을 제공하는 함수다.
