# Recoil
Rcoil은 페이스북이 2020년에 소개한 React전용 상태 관리 라이브러리다.  
  
contextAPI는 상태를 전달할 때 객체형태의 value를 사용한다. 
따라서 객체 안의 값이 하나라도 변경되면 provider로 감싼 모든 하위 컴포넌트가 리렌더링 된다는 단점이 있다.  
하진만 Recoli의 경우 각각 전역 상태에 대한 atom이 생성되고 해당 상태를 구독하는 구성요소만 리렌더링 된다.  
이로써 불필요한 리렌더링을 방지할 수 있다.

## 설치
```bash
$ npm install recoil
```
```bash
$ yarn add recoil
```

## 주요개념
### data-flow graph
상태 데이터가 atoms -> selectors -> 컴포넌트 순서로 흐르는 것을 말한다.
