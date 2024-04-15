# Redux(리덕스)
> javascript 상태관리 라이브러리

### Redux의 기본개념:3가지 원칙
#### 1. 단일 스토어(Single source of truth)
+ 애플리케이션의 모든 상태는 하나의 저장소 안에 하나의 객체트리 구조로 저장된다.
#### 2. 읽기 전용 상태(State is read-only)
+ 상태는 불변하며, 오직 Action만이 상태교체를 요청할 수 있다.
#### 3. 리듀서는 순수한 함수(Changes are made with pure functions)
+ 변화는 순수함수 (Reducer)로 작성되어야 한다.
  - 리듀서 함수는 이전 상태와 액션객체를 파라미터로 받는다.
  - 파라미터 외의 값에는 의존X

### 1.Store(스토어) 
> Store는 상태가 관리되는 오직 하나의 공간이다.(한개의 프로젝트에는 한개의 스토어만 가능)
  - 컴포넌트와는 별개로 스토어라는 공간이 있어 그 스토어 안에 앱에서 필요한 상태를 담는다.
  - 컴포넌트에서 상태정보가 필요할 때 스토어에 접근한다.
  - 스토어 안에는 현재 애플리케이션 상태와 리듀서가 필수적으로 들어가야한다.
  - 그 외에도 몇가지 중요한 내장함수가 들어간다.
  
### 2.Action(액션) 
> Action은 앱에서 스토어에 운반할 데이터를 말한다. Action은 자바스크립트 객체형식으로 되어있다.
+ 상태에 어떠한 변화가 필요하면 액션이라는 것이 발생한다, 이는 아래처럼 하나의 객체로 표현된다.
```js
{
  type: 'TOGGLE_VALUE'
}
```
+ 액션 객체는 type필드를 반드시 가지고 있어야한다. 이 값을 액션의 이름이라고 생각하면 된다. 
+ 그 외의 값들은 나중에 상태 없데이트를 할 때 참고하는 값이며 작성자 마음대로 넣을 수 있다.
 ```js
 {
   type: 'ACTION_CHANGE_USER',
   payload: { //option
     name: '홍길동',
     age: 100
   }
 } 
 ```
 
### 2.1.Action Creator(액션생성함수)
> 액션 생성 함수는 액션 객체를 만들어주는 함수 이다.
```js
function addTodo(data) {
  return {
    type: 'ADD_TODO',
    data
  };
}

//화살표 함수로도 만들 수 있음
const ChangeInput = text =>({
  type: 'CHANGE_INPUT',
  text
});
```
+ 변화를 일으킬 때 마다 액션 객체를 만들어야 하는데 매번 직접 작성하다보면 실수를 할 가능성이 높아지므로 방지하기 위해 함수로 만들어 관리한다.

### Reducer(리듀서) 
> 변화를 일으키는 함수다. 액션을 만들어서 발생시키면 리듀서가 현재 상태와 전달받은 액션 객체를 파라미터로 받아 온다. 그리고 그 두 값을 참고해 새로운 상태를 반환한다.

  - Action을 바로 Store에 전달하는 것이 아닌 Reducer에 전달한후 Reducer가 주문을 보고 Store의 상태를 업데이트하는 것이다.
  - Action을 Reducer에 전달하기 위해서는 dispatch()메소드를 사용해야한다.
```js
const initialState= {
  counter: 1
};
function reducer(state = initialState, action){
  switch (action.type) {
    case INCREMENT:
      return {
        counter: state.counter + 1
      };
    default:
      return state;
  }
}
```

### dispatch(디스패치)
> 스토어의 내장 함수중 하나다. `액션을 발생시키는것`이라 생각하면 된다.
- 이 함수가 호출되면 스토어는 리듀서 함수를 실행시켜 새로운 상태로 만들어준다.

### subscribe(구독)
> 스토어의 내장 함수중 하나다. subscribe 함수안에 리스너 함수를 파라미터로 넣어서 호출해주면 이 함수가 액션이 디스패치되어 업데이트될 때마다 호출된다.
+ 디스패치 될때마다 실행
```js
const Listener = () => {
  console.log('상태가 업데이트됨');
}
const unsubscribe = store.subscribe(listener);

unsubscribe();// 나중에 구독을 비활성화 할 때 함수를 호출
```
