# Suspense
> React v18.0에서 정식으로 추가된 기능으로 컴포넌트의 랜더링을 어떤 작업이 끝날 때까지 잠시 중단시키고 다른 컴포넌트를 먼저 랜더링할 수 있습다. 
## 기본문법
```js
<Suspense fallback={<spinner/>} >
    <UserList />
</Suspense>
```
+ Suspense로 감싸므로써 컴포넌트의 랜더링을 특정 작업 이후로 미루고, 작업이 끝날 때 까지 fallback속성으로 넘긴 컴포넌트를 대신 보여준다.