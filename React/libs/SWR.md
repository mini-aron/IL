# SWR 
vercel에서 제작한 데이터를 가져오기 위한 모듈이다.
SWR의 기본적인 작동은 우선 캐시(stale)에서 데이터를 불러오고, 검증을 위한 요청(revalidate)을 보내고, 마침내 최신 데이터로 업데이트하는 과정을 거친다.   
또한 SWR을 사용하는 컴포넌트들은 지속적이고 자동적으로 데이터 업데이트가 이루어짐으로써 항상 최신 상태를 유지할 수 있게 된다.

### 설치
```bash
$ npm i swr
$ yarn add swr
```

## 사용법

```js
const { data, error } = useSWR(key, fetcher);
```

### key
> 요청을 보낼 주소를 의미한다.

```js
const { data, error } = useSWR("/api/data", fetcher);
```

### fetcher
> swr의 핵심적인 API로, key를 받아 데이터를 반환하는 비동기 함수다.  
> 이 fetcher에는 데이터 패칭에 사용되는 axios,GraphQL등 어떤 라이브러리든 쓸수있다.
```js
const fetcher = (url) => fetch(url).then((res) => res.json());

const { data, error } = useSWR(key, fetcher);
```

### data
> useSWR에 의해 반환된 데이터를 의미한다.

### error
> 데이터를 패칭하는 과정에서 오류가 발생할 시 반환된다.

## 전역으로 fetcher 설정하기
> 매번 fetcher를 선언하기 번거로울때 SWRconfig를 통해 전역 fetcher을 설정할 수 있게 해준다.
```js
<SWRConfig value={options}>
  <Component />
</SWRConfig>
```
```js
function App() {
  const options = {
    fetcher: (resource, init) =>
      fetch(resource, init).then((res) => res.json()),
  };
  return (
    <SWRConfig value={options}>
      <Home />
    </SWRConfig>
  );
}
```
```js
function Home() {
  const { data: first } = useSWR(firstKey);
  const { data: second } = useSWR(secondKey);
}
```