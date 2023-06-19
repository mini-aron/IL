# 미들웨어(middleware)
리덕스 미들웨어는 [액션](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#2action%EC%95%A1%EC%85%98)을 [디스패치](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#dispatch%EB%94%94%EC%8A%A4%ED%8C%A8%EC%B9%98)했을 때 [리듀서](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#reducer%EB%A6%AC%EB%93%80%EC%84%9C)에서 이를 처리하기에 앞서 `사전에 지정된 작업들을 실행`한다.  
미들웨어는 액션과 리듀서 사이의 중간자 라고 볼 수 있다.

![image](https://github.com/mini-aron/IL/assets/105274015/098b2592-8e9c-4cda-9fd8-aa8ead6d53e7)

리듀서가 [액션](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#2action%EC%95%A1%EC%85%98)을 처리하기 전에 미들웨어가 할 수 있는 작업은 여러가지가 있다.  
전달맏은 [액션](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#2action%EC%95%A1%EC%85%98)을 단순히 콘솔에 기록하거나, 전달받은 [액션](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#2action%EC%95%A1%EC%85%98)정보를 기반으로 액션을 취소하거나,  
다른종류의 [액션](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#2action%EC%95%A1%EC%85%98)을 추가로 디스패치 할 수 있다.

## 다양한 미들웨어들
### redux-thunk
+ 리덕스를 사용하는 프로젝트에서 가장 기본적으로 사용하는 미들웨어
#### thunk
> thunk는 특정 작업을 나중에 할 수 있도록 미루기 위해 함수형태로 감싼 것을 의미한다.

#### counter 예시
적용 전
```js
const addOne = x => x + 1;
addOne(1);
```
적용 후
```js
const addOne = x => x + 1;  //연산
function addOneThunk (x){  //연산하고 반환
  const thunk = () => addOne(x);
  return thunk;
}

const fn = addOneThunk(1);//fn에 넣으면
setTimeout(() => {
  const value = fn(); //fn이 실행되는 시점에 연산된다.
  console.log(value);
}, 1000)
```
#### redux-thunk lib
> redux-chunk라이브러리를 사용하면 thunk함수를 만들어 디스패치할 수 있습니다.
> 그러면 리덕스 미들웨어가 그 함수를 전달받아 store의 dispatch와getstate를 파라미터로 넣어서 호출 해 줍니다.
```js
const sampleThunk = () => (dispatch, getState) => {
  //현제상태를 참조할 수 있고,
  //새 액션을 디스패치 할 수도 있다.
}
```
