## LifeCycle
>라이프사이클은 총3 가지 ,마운트,업데이트,언마운트카테고리로 나뉜다.

### 마운트(mount)
#### 마운트할 때 호출하는 메서드
>컴포넌트 만들기 => ```constructor``` => ```getDerivedStateFromProps``` => ```render``` => ```componentDidMount```
+ ```constructor```: 컴포넌트를 사로 만들 때마다 호출되는 클래스 생성자
+ ```getDerivedStateFromProps```: ```props```에 있는 값을 ```state```에 넣을 때 사용하는 메서드
+ ```render```: 우리가 준비한 UI를 렌더링 하는 메서드
+ ```componentDidMount```: 컴포넌트가 웹 브라우저상에 나타난 후 호출하는 메서드

### 업데이트(update)
+ ```props```가 바뀔때
+ ```state```가 바뀔때
+ 부모 컴포넌트가 리렌더링 될때
+ ```this.forceUpdate```로 강제로 렌더링을 트리거할 때



