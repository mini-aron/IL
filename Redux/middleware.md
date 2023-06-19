# 미들웨어(middleware)
리덕스 미들웨어는 [액션](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#2action%EC%95%A1%EC%85%98)을 [디스패치](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#dispatch%EB%94%94%EC%8A%A4%ED%8C%A8%EC%B9%98)했을 때 [리듀서](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#reducer%EB%A6%AC%EB%93%80%EC%84%9C)에서 이를 처리하기에 앞서 `사전에 지정된 작업들을 실행`한다.  
미들웨어는 액션과 리듀서 사이의 중간자 라고 볼 수 있다.

![image](https://github.com/mini-aron/IL/assets/105274015/098b2592-8e9c-4cda-9fd8-aa8ead6d53e7)

리듀서가 [액션](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#2action%EC%95%A1%EC%85%98)을 처리하기 전에 미들웨어가 할 수 있는 작업은 여러가지가 있다.  
전달맏은 [액션](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#2action%EC%95%A1%EC%85%98)을 단순히 콘솔에 기록하거나, 전달받은 [액션](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#2action%EC%95%A1%EC%85%98)정보를 기반으로 액션을 취소하거나,  
다른종류의 [액션](https://github.com/mini-aron/IL/blob/main/Redux/Redux.md#2action%EC%95%A1%EC%85%98)을 추가로 디스패치 할 수 있다.
