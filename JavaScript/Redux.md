## Redux(리덕스)
> javascript 상태관리 라이브러리

### Redux의 기본개념:3가지 원칙
1. Single source of truth
> 애플리케이션의 모든 상태는 하나의 저장소 안에 하나의 객체트리 구조로 저장된다.
2. State is read-only
> 상태는 불변하며, 오직 Action만이 상태교체를 요청할 수 있다.
3. Changes are made with pure functions
> 변화는 순수함수 (Reducer)로 작성되어야 한다.

+ Store(스토어) : Store는 상태가 관리되는 오직 하나의 공간이다.
  - 컴포넌트와는 별개로 스토어라는 공간이 있어 그 스토어 안에 앱에서 필요한 상태를 담는다.
  - 컴포넌트에서 상태정보가 필요할 때 스토어에 접근한다.
+ Action(액션) : Action은 앱에서 스토어에 운반할 데이터를 말한다. Action은 자바스크립트 객체형식으로 되어있다.
  ``` 
  {
    type: 'ACTION_CHANGE_USER',
    payload: { //option
      name: '홍길동',
      age: 100
    }
  } 
  ```
+ Reducer(리듀서) 
  - Action을 바로 Store에 전달하는 것이 아닌 Reducer에 전달한후 Reducer가 주문을 보고 Store의 상태를 업데이트하는 것이다.
  - Action을 Reducer에 전달하기 위해서는 dispatch()메소드를 사용해야한다.

