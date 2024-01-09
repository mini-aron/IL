# react-query
> 서버의 값을 클라이언트에 가져오거나, 캐싱, 값 없데이트, 에러핸들링 등 비동기 과정을 더욱 편하게 하는데 사용된다.

## react-query 장점
+ 캐싱
+ get을 한 데이터에 대해 update를 하면 자동으로 get을 다시 수행한다.(ex)게시판의 글을 가져왔을 때 게시판의 글을 생성하면 게시판의 글을 get하는 api를 자동으로 실행)
+ 데이터가 오래되었다고 판단되면 다시 get
+ 동일 데이터를 여러번 요청하면 한번만 요청
+ 무한스크롤
+ 비동기 과정 선언적 관리 가능
+ react hook과 사용하는 구조 유사

## 캐싱(Caching)
> 캐싱이란 특정 데이터의 복사본을 저장하여 이후 동일한 데이터의 재접근 속도를 높이는 것을 말한다.

React-query는 캐싱을 통해 동일한 데이터에 대한 반복적인 비동기 데이터 호출을 방지하고, 이는 불필요한 api콜을 줄여 서버에 대한 부하를 줄이는 좋은 결과를 가져온다.

### 데이터 갱신
서버 데이터를 불러와 캐싱 후, 실제 서버 데이터를 확인했을 때 서버 상에서 데이터의 상태가 변경되어있다면, 사용자는 실제 데이터가 아닌 변경전 데이터를 볼 수 밖에 없다.  
이런 상황을 방지하기위해 적절한 데이터 갱신이 필요하다.  
  
### react-query의 옵션
```
refetchOnWindowFocus, //default: true
refetchOnMount, //default: true
refetchOnReconnect, //default: true
staleTime, //default: 0
cacheTime, //default: 5분 (60 * 5 * 1000)
```
+ 브라우저에 포커스가 들어온 경우(refetchOnWindowFocus)
+ 새로운 컴포넌트 마운트가 발생한 경우(refetchOnMount)
+ 네트워크 재연결이 발생한 경우(refetchOnReconnect)

#### staleTime
> 데이터가 fresh -> stale 상태로 변경되는 데 걸리는 시간이다.
+ fresh상태일 때는 Refeth 트리거가 발생해도 Refetch가 일어나지 않는다.
+ 기본값이 0이기 때문에 따로 설정하지 않으면 Refetch 트리거가 발생시 무조건 Refetch가 발생한다.

#### cacheTime
> 데이터가 inactive한 상태일 때 캐싱된 상태로 남아있는 시간이다.
+ 특정 컴포넌트가 unmount되면 사용된 데이터는 inactive상태로 바뀌고, 이때 데이터는 cacheTime만큼 유지된다.
+ cacheTime 이후 데이터는 가비지 콜렉터로 수집되어 메모리에서 해제된다.
+ 만일 cacheTime이 지나지 않았는데 해당 데이터를 사용하는 컴포넌트가 mount되면 새로운 데이터를 fetch해오는 동안 캐싱된 데이터를 보여준다.

## Client 데이터와 Server 데이터 간의 분리
>  Client 데이터의 경우 Redux, Recoil, mobX와 같은 전역 상태 관리 라이브러리들을 통해 잘 관리되고있지만, 이런 라이브러리들이 Server데이터까지 관리를 해야하는 상황이 발생하기도 한다.  
위의 라이브러리들은 Client 데이터를 관리하는데 로직이 집중되어있기 때문에, Server 데이터까지 효율적으로 관리하기에는 한계가 분명하다.


## SWR과의 차이

### SWR
```js
import useSWR from "swr";

const App = () => (
  <div>
    <SWRProfile />
  </div>
);

const SWRProfile = () => {
  const {data, error} = useSWR("https://61b88c9d64e4a10017d19053.mockapi.io/user", url =>
    fetch(url).then(res => res.json())
  );

  if (error) return <div>failed to load</div>;
  if (!data) return <div>loading...</div>;

  return <Profile library="SWR" data={data} />;
}

const Profile = ({library, data}) => (
  <div>
    <h1>Users from {library}</h1>
    {data.map(user => <p>{user.level} developer <strong>{user.name}</strong></p>)}
  </div>
)

export default App;
```
### React-Query
```js
import { QueryClient, QueryClientProvider, useQuery } from "react-query";

const queryClient = new QueryClient();
const url = "https://61b88c9d64e4a10017d19053.mockapi.io/user";

const App = () => (
  <div>
    <QueryClientProvider client={queryClient}>
      <ReactQueryProfile />
    </QueryClientProvider>
  </div>
);

const ReactQueryProfile = () => {
  const {isLoading, error, data, isFetching} = useQuery("users", () =>
    fetch("https://61b88c9d64e4a10017d19053.mockapi.io/user").then(res => res.json())
  );

  if (error) return <div>failed to load</div>;
  if (isLoading) return <div>loading...</div>;

  return <Profile library="React Query" data={data} />;
}

const Profile = ({library, data}) => (
  <div>
    <h1>Users from {library}</h1>
    {data.map(user => <p>{user.level} developer <strong>{user.name}</strong></p>)}
  </div>
)

export default App;
```

### SWR의 장점
#### Provider
SWR은 별도의 Provider 없이 바로 사용이 가능하나 React-Query는 기본적으로 컴포넌트를 감싸는 별도의 Provider가 필요해 설정해야한다.

#### Fetcher
useSWR과 useQuery모두 두번째 인자로 fetcher를 받는다.  
이때 SWR의 경우 첫번째 인자로 url을 받고, 두번째 인자인 fetcher에 받은 url을 넘겨주는 방식을 사용한다. 또한 SWR은 전역설정을 통해 fetcher를 정해둘 수 있다.  
하지만 React-Query는 fetcher에 url을 직접 전달해줘야한다.

### React-Query의 장점
#### Devtools
React-Query에선 공식적으로 react-query/devtools 을 통해 Devtool을 지원한다.  
개발모드에서만 사용하며, devtools를 통해 더 확실하게 데이터의 흐름을 파악할 수 있다.  
SWR또한 devtools를 사용할 수 있으나, 서드 파티 라이브러리를 이용해야한다.

#### 무한 스크롤 구현
SWR과 React-Query 모두 무한 스크롤을 구현하는데 필요한 기능들을 제공한다.  
그러나 SWR로 무한 스크롤을 구현할려면 부가적인 코드를 작성해야하는 반면, React-Query에서는 getPreviousPageParam, fetchPreviousPage, hasPreviousPage 와 같은 다양한 페이지 관련 기능이 존재해 이를 이용해 무한 스크롤을 쉽게 구현 가능하다.  

##### Selectors 
React-Query에서는 select 키워드를 사용해 raw data로부터 원하는 데이터를 추출해 반환할 수 있다. 
```js
import { useQuery } from 'react-query'

function User() {
  const { data } = useQuery('user', fetchUser, {
    select: user => user.username,
  })
  return <div>Username: {data}</div>
}
```
👆 위의 예시처럼 select 를 통해 원하는 데이터에 접근한 뒤 추출이 가능하다  

#### Data Optimization
SWR과 다르게 React-Query는 쿼리가 업데이트 될 때만 refetch를 진행한다.  
또한 여러 컴포넌트에서 동일한 쿼리를 사용하는 경우 한번에 묶어 업데이트를 진행한다.  
이를 통해 렌더링 퍼포먼스를 개선시킨다.  

#### Garbage Collection
React-Query는 지정된 시간동안 쿼리가 사용되지 않는다면 자동으로 메모리 해제를 하는 Auto Garbage Collection을 통해 메모리를 관리해준다.