### useEffect

+ 컴포넌트가 마운트/언마운트 될 때를 제어가능
+ 컴포넌트의 props나 상태가 바뀌어 업데이트 되기전과 될때에도 작업가능
+ 리렌더링 될 때 마다 작업가능 

### basic
```
useEffect(()=>{
  (수행되는 작업)
}, [의존값])
```
#### use
```
useEffect(() => {
 //monut
 console.log('컴포넌트 나타남');
 
 return() => {
 //unmount
 console.log('컴포넌트 사라짐');
 }
}, [])
```
### mount/ unmount use
#### mount
+ 받아온 props를 객체의 state로 설정
+ 외부 api 요청(REST API 등)
+ 라이브러리 사용(d3, video.js 등)
+ setInteval 을 통한 반복작업 또는 setTimeout을 사용한 작업 예약

#### unmount
+ 뒷정리 함수
+ clearInterval, clearTimeout 을 사용해 등록한 작업 clear
+ 라이브러리 인스턴스 제거

### deps
+ 두번째 파라미터에 들어가는 의존값

#### deps에 특정값 넣기

```

```
