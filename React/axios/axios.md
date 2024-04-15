### axios
>node.js와 브라우저를 위한 promise Api기반 http비동기 통신 라이브러리
#### 특징
+ http요청과 응답을 ```JSON```형태로 자동변환
+ 운영 환경에 따라 브라우저의 ```XMLHttpRequest```객체 또는 Node.js의 http api 사용
+ 요청과 응답 데이터의 변형
+ http 요청 취소
#### basic
```
axios({
  url:'https://.....',  //통신api주소
  method: 'get',        //통신방식
  data: { //인자로 보낼 데이터
    test: bolean
  }
})
```
#### axios request prameter option

### axios vs fetch
|axios|fetch|
|------|---|
|써드파티 라이브러리로 설치 필요|설치가 필요없음|
|XSRF보호를 해줌|보호없음|
|data속성 사용|body속성 사용|
|data는 object를 포함|body는 문자열화 되있음|
|status가200,statusText가'OK'이면 성공|응답객체가 ok속성을 포함하면 성공|
|자동JSON형변환|.JSON()메서드를 사용해야함|
|요청최소 가능,타임아웃 걸 수 있음|해당기능 없음|
|HTTP요청을 가로챌수 있음|기본적으로 제공X|
|download진행에 대해 기본적인 지원O|지원X|
|많은 브라우저 호환|Chrome 42+, Firefox 39+, Edge 14+, and Safari 10.1+이상에 지원|

