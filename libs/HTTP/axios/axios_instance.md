# axios instance
HTTP요청을 보내는 데 사용되는 설정을 정의하고 관리하는데 사용된다.  
인스턴스를 사용해서 여러 요청에서 같은 설정을 사용하고, 중복코드가 나오지 않고 효율적으로 관리할 수 있게 해준다!
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




