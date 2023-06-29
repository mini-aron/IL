# useSelector
connect함수를 사용하지않고 상태를 조회할 수 있게 도와주는 hook이다.

### 사용법
```js
import { useSelector } from "react-redux";

const CounterContainer = () => {
    const number = useSelector((state) => state.counter.number);
    return <p>{number}</p>;
}

export default CounterContainer;
```