### useRef
>특정 DOM을선택해야 할 때, ref를 사용해야한다
>그리고 이를 설정할때 useRef를 사용해 설정한다
### 역할,용도
+ DOM을 선택하는 용도
+ 컴포넌트 안에서 조회 및 수정할 수 있는 변수 관리
### caution
+ useRef로 관리하는 변수는 값이 바뀐다 해서 컴포넌트 상태가 리렌더딩 되지않는다.
+ useRef로관리하는 변수는 설정후 바로 조회 가능
### management
+ ```setTimeout```,```setInterval```을 통해서 만든```id```
+ 외부 라이브러리를 사용해 생성된 인스턴스
+ scroll 위치
