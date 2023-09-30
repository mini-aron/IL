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
