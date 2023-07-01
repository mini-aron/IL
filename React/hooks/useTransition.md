# useTransition
useTrasition은 상태 값을 관리하거나 우선순위를 정할때 사용한다.
useTransition에서 반환하는 두 번째 파라미터의 함수인 startTransition으로 감싼 함수는
함수가 실행되는 동일한 경우, 더욱 낮은 우선순위로 실행된다.
```js
function App() {
    const [isPending,startTransition] = useTransition();
    const [value, setValue] = useState(0);

    function Click() {
        startTransition(() => {
            setCount(value + 1);
        })
    }

    return(
        <div>
            <button onClick={onClick}>{count}</button>
        </div>
    );
}
```
첫 번째 파라미터에는 지연 상태를 나타내는 isPendig, 두 번째는 함수를 지연시키는 함수로 구성되어있다.
이 훅을 통해서 지연 상태를 확인하고, 로딩 중인 화면을 따로 보여주거나 하는 등의 서비스를 구현할 수 있다.