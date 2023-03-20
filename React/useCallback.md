### useCallback
>useCallback은 useMemo와 비슷한 Hook입니다. useMemo는 특정 결괏값을 재사용할 때 사용하는 반면,  useCallback은 특정 함수를 새로 만들지 않고 재사용하고 싶을 때 사용하는 함수입니다.
### basic
```
const memoizedCallback = useCallback(함수, 배열);
```
