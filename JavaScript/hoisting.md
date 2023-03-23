## hoisting
>변수와 함수 선언이 스코프(SCOPE)의 최상단으로 올려져 실행되는 것

### 변수 생성 단계
+ 선언 단계(Declaration Phase): 변수 객체를 실행 컨텍스트에 등록한다. 
+ 초기화 단계(Initialization Phase): 등록된 변수의 메모리를 확보한다. (변수는 ```undefined```로 초기화된다.) 
+ 할당 단계(Assignment Phase): 초기화된 변수에 실제 값을 할당한다.
