# beforeunload

beforeunload이벤트는 사용자가 페이지를 떠날 때 발생한다.  
+ 새로고침
+ 뒤로가기
+ 브라우저 닫기
+ form submit 
등등  

## 문법
```js
window.onbeforeunload = (event) => {
    //실행시킬 코드
};
```