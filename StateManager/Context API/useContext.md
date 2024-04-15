# useContext
useContext는 context api의 기능중 하나로 컴포넌트 밖에서도 값을 핸들링하고 파싱할 수 있다.

```js
const userInfo = {
  id: 3,
  name: "hong",
  isLogin: false,
};
const UserContext = createContext(userInfo);
```

```js
const MyPage = () => {
  const user = useContext(UserContext);

  return (
    <div>
      <h1>유저 아이디 : {user.id}</h1>
      <h1>이름 : {user.name}</h1>
      <h1>{user.isLogin ? "로그인중" : "로그인하지않음"}</h1>
    </div>
  );
};
```