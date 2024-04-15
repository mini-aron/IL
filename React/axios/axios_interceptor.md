
# axios interceptor
인터셉터는 요청과 응답을 가로채고 수정하는 기능을 제공한다.

## 예시
요청 인터셉터와 응답 인터셉터가 나뉘어져있다.
```js
// 요청 인터셉터 추가
axios.interceptors.request.use(
    function (config) {
        //요청을 보내기 전에 수행 할 일
        return config;
    },
    function (error) {
        //오류 요청을 보내기전 수행할 일
        return Promise.reject(error);
    });

// 응답 인터셉터 추가
axios.interceptors.response.use(
    function (response) {
        //응답데이터를 가공
        return response;
    },
    function (error) {
        //오류 응답을 처리
        return Promise.reject(error);
    });
```
