## Rewrites
> 특정 Url을 직접 입력하면 다른 Url로 이동하지만, 사용자에게는 마치 이동이 되지 않은 것 처럼 보여준다.
> 특정 Url을 Masking하면서 다른 Url을 보여주는 것이다.

### 장점
+ 외부API통신을 할 때 사용되는 Key의 관리기 용이하다.
+ Next.js에서 외부 Api를 호출할 때 발생하는 CORS 이슈를 처리하는데 한가지 방법중 하나다.

### ex)
```js
module.exports = {
  async rewrites() {
    return [
      {
        source: '사용할 주소',
        destination:'실제 API주소',
      },
    ]
  },
}
```
+ next.config.js파일에서 module.export Object안에 async를 선언하고 Return Array안에 지정해주면 된다.
