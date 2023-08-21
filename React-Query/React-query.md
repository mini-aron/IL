# React-Query
React query는 React Application에서 서버 상태를 불러오고, 캐싱하며 지속적으로 동기화하고 업데이트하는 작업을 도와주는 라이브러리이다.
.

## react-query 장점
주로 아래와 같은 구현하기 귀찮은 일을 수행한다.  
+ 캐싱
+ get을 한 데이터에 대해 update를 하면 자동으로 get을 다시 수행한다.  
(ex. 게시판의 글을 가져왔을때 게시판의 글을 생성하면 게시판 글을 get하는 api를 자동으로 실행)  
+ 데이터가 오래 되었다고 판단시 다시 get  
(invalidateQueries)  
+ 동일 데이터 여러번 호출시 한번만 요청한다.  
(옵션에 따라 중복 호출 허용 시간 조절 가능)  
+ 무한 스크롤  
+ 비동기 과정을 선언적으로 관리 가능
+ react hook과 사용하는 구조가 비슷함

## 사용법
```bash
$ yarn install react-query
$ npm install react-query
```
먼저 react의 가장 기본이 되는 곳에 세팅한다.
```js
// src/index.js
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";
import { QueryClient, QueryClientProvider } from "react-query";
import { ReactQueryDevtools } from "react-query/devtools";

const queryClient = new QueryClient();

ReactDOM.render(
  <React.StrictMode>
    <QueryClientProvider client={queryClient}>
      {/* devtools */}
      <ReactQueryDevtools initialIsOpen={true} />
      <App />
    </QueryClientProvider>
  </React.StrictMode>,
  document.getElementById("root")
);

```

## useQuery
데이터를 get 하기 위한 api이다.  
post, update는 useMutation을 사용한다.  
### 정보
1. 철번째 파라미터: unique Key 
    + 호출을 위한 키로 다른 컴포넌트에서도 해당 키를 사용하면 호출 가능하다.
    + String과 배열을 받는다.  
    배열로 넘기면 0번 값은 string값으로 다른컴포넌트에서 부를 값이 들어가고  
    두번째 값을 넣으면 query함수 내부에 파라미터로 해당 값이 전달된다.  
2. 두번째 파라미터: 비동기 함수(api호출 함수 - promise)
3. 세번째 파라미터: 옵션이 들어간다.
    + enabled를 사용하면 동기적으로 사용 가능하다.
4. return 값은 api의 성공,실패여부, api return값을 포함한 객체이다.  
5. usequery는 비동기로 작동한다.  


```js
const Todos = () => {
  const { isLoading, isError, data, error } = useQuery("todos", fetchTodoList, {
    refetchOnWindowFocus: false, // react-query는 사용자가 사용하는 윈도우가 다른 곳을 갔다가 다시 화면으로 돌아오면 이 함수를 재실행합니다. 그 재실행 여부 옵션 입니다.
    retry: 0, // 실패시 재호출 몇번 할지
    onSuccess: data => {
      // 성공시 호출
      console.log(data);
    },
    onError: e => {
      // 실패시 호출 (401, 404 같은 error가 아니라 정말 api 호출이 실패한 경우만 호출
      // 강제로 에러 발생시키려면 api단에서 throw Error 날림
      console.log(e.message);
    }
  });

  if (isLoading) {
    return <span>Loading...</span>;
  }

  if (isError) {
    return <span>Error: {error.message}</span>;
  }

  return (
    <ul>
      {data.map(todo => (
        <li key={todo.id}>{todo.title}</li>
      ))}
    </ul>
  );
};

```
#### isLoading, isSuccess 말고 status로 한번에 처리 하는 방법

```js
function Todos() {
  const { status, data, error } = useQuery("todos", fetchTodoList);

  if (status === "loading") {
    return <span>Loading...</span>;
  }

  if (status === "error") {
    return <span>Error: {error.message}</span>;
  }

  return (
    <ul>
      {data.map(todo => (
        <li key={todo.id}>{todo.title}</li>
      ))}
    </ul>
  );
}
```
#### useQuery 동기적 실행
```js
const { data: todoList, error, isFetching } = useQuery("todos", fetchTodoList);
const { data: nextTodo, error, isFetching } = useQuery(
  "nextTodos",
  fetchNextTodoList,
  {
    enabled: !!todoList // true가 되면 fetchNextTodoList를 실행한다
  }
);
```