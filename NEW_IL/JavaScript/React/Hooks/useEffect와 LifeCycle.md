## LifeCycle Method

> 다음 세개의 메소드가 핵심이다.
> 1. 컴포넌트가 마운트 될 때 : componentDidMount
> 2. 컴포넌트가 리렌더링될 때 : componentDidUpdate
> 3. 컴포넌트가 마운트 해제되기 전에 : componentWillunmount

LifeCycle Method 는 생명주기 메서드라고 불린다.
컴포넌트가 브라우저상에 나타나고, 업데이트되고, 사라지게 될 때 호출되는 메서드이다.
추가로 컴포넌트에 에러가 났을 때 호출되는 메서드도 있다.

![[Pasted image 20240116223603.png]]

### 1. Mounting
component가 새롭게 생성되는 시점이다 Component 함수가 실행되고 결과물로 나온 Element들이 가상Dom 에 삽입되고 실제 Dom을 업데이트하기까지의 과정이다. 여기서 Mount는 컴포넌트가 처음 실행된걸 말한다.

+ **counstructor()** : 컴포넌트의 초기 state값을 정의한다. 컴포넌트에서 사용되는 이벤트 핸들러를 바인딩한다.
+ **render()** : this.props와 this.state 값을 검증하여 반환값을 화면에 렌더링시킨다. render()함수 내부에서 this.state를 변경시키면 무한 업데이트가 일어날 수 있기때문에 순수함수로 작성되어야한다.
+ **componentDidMount()** : componentDidMount()는 컴포넌트가 최초로 마운팅 된 이후 1회 실행된다. 그래서 다음과 같은 목적을 위해 주로 사용된다.
### 2. Update
Component들은 state나 props가 변경되면 update가 진행되며 다시 rendering된다.

component가 update될 때 아래의 순서대로 메소드가 실행이 된다.  
1. New Props / setState()  
2. render()  
3. componentDidUpdate()

- **New Props / setState()** : 상위 Component로부터 갱신된 props 를 받는 경우 / 현재 자신이 가진 state를 변경하는 경우
    
- **componentDidUpdate** : `componentDidUpdate` 는 update 가 이루어지고 render가 완료된 직후 실행되는 메소드이다. 최초 마운트 될 때는 실행되지 않는다.
    

`componentDidUpdate` 를 이용할 때, `setState`를 주의해야 한다. 조건문 등으로 제어해두지 않으면 무한 루프에 빠질 수 있기 때문이다.

setState > componentDidupdate > SetSate ...
### 3. Unmount(제거)

해당하는 Component가 `DOM상에서 제거`가 될 때 실행되는 lifeCycle이다.

주로 componentDidMount()에서 등록한 이벤트 리스너, setInterval, setTimeout을 클리어 하거나 외부 라이브러리 인스턴스 제거 등에 사용된다.

# useEffect

React Hook에서는 `useEffect`를 통해 react클래스의 componentDidMount나 componentDidUpdate, componentWillUnmount와 같은 목적으로 `lifeCycle`를 관리한다.

## useEffect deps

![[Pasted image 20240116224402.png]]

### 1. useEffect deps가 빈 배열의 경우

```javascript
useEffect(() => {
  
}, [])
```

useEffect deps가 빈 배열의 경우 `처음 Mount(첫 rendering)` 될 때 호출된다.  
`componentDidMount()`와 비슷하다.