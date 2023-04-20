## Redirects
> redirect ( re(다시) + direct(지시하다) ) 말 그대로 다시 지시하는 것을 말한다.

#### ex)
1. ```www.nav*r.com/pageA``` 요청을 보냄
  - 브라우저 -> server
2. ```www.nav*r.com/pageB``` 로 redirect시킴
  - server -> 브라우저
3. ```www.nav*r.com/pageB``` 요청을 보냄
  - 브라우저 -> server

## NEXT의 Redirects

```js

 module.exports = {
  async redirects() {
    return [
      {
        source: '기존주소',
        destination: '이동할주소',
        premanent: 브라우저,검색엔진의 기억여부(true,flase),
      },
    ]
  },
 }
```
+ next,config.js파일에서 module.export Object안에 redirets()함수선언

```js
 module.exports = {
  async redirects() {
    return [
      {
        source: '/old-blog/:path*',
        destination: '/new-blog/:path*',
        premanent: flase,
      },
    ]
  },
 }
```
+ 뒤에 :path*를 설정하여 Redirect하는 방식이다.
+ ``` /old-blog/111``` --redirect-> ```/new-blog/111```
+ 맨 뒤에*를 붙여주는 것은 모든 Query String을 Catch해준다는 뜻이다. ex)  ```/old-blog/123?key=123``` --redirect-> ```/new-blog/123?key=123```
