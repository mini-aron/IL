# console
> 노드에서 console은 window대신 global객체가 들어있으며 브라우저의console과 거의 비슷하다.  

## 여러가지 console들
+ console.time(레이블) : console.timeEnd와 대응되어 같은 레이블을 가진 time과 timeEnd사이의 시간을 측정한다.
+ console.log(내용) : 평벙한 로그를 콘솔에 표시한다. console.log(내용,내용..)처럼 여러 내용을 동시에 표현 가능하다.
+ console..error(에러 내용) : 에러를 콘솔에 표시한다.
+ console.table(배열) : 배열의 요소로 객체 리터럴을 넣으면, 객체의 속성들이 테이블 형식으로 표현된다.
+ console.dir(객체, 옵션) : 객체를 콘솔에 표시할 때 사용한다. 첫번째 인수는 표시할 객체, 두번쨰 인수로 옵션을 넣는다.
+ console.trace(레이블) : 에러가 어디서 발생했는지 추적할 수 있게 한다.
