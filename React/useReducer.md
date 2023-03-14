### useReducer
>```useReducer```는```useState```보다 더 다양한 컴포넌트 상황에 따라 다양한 상태를 다른 값으로 업데이트 해 주고 싶을 때 사용하는 Hook
+ 리듀서는 현재 상태, 업데이트를 위해 필요한 정보를 담은 액션(action)값을 전달받아 새로운 형태로 변환하는 함수
+ 리듀서 함수에서 새로운 상태를 만든다면 반드시 불변성을 지켜 주여야 함

#### 리듀서 형태
```
function reducer(state,action){
  return{ ... };
}
```
#### 액션값 형태
```
{
  type: 'INCREMENT',
  //다른값이 필요하다면 추가로 들어감
}
```
### example
```
```
