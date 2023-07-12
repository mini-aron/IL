# axios instance
Axios의 인스턴스를 생성

## axios.create
```js
axios.create([config])
```
### 예시
```js
const instance = axios.create({
    baseURL: 'https://some-domain.com/api/',
    timeout: 1000,
    headers: {'X-Custom-Header': 'foobar'}
});
```




