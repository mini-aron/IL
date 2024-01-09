### useState

+ state: 컴포넌트 에서의 동적인 값
+ 컴포넌트 에서의 상태관리를 위한 함수

```
import React,{ useState } from 'react';
// useState import from react pakage 


const [값변수, 값변경함수] = useState(기본값);

const 값변경함수 = () => {
 //변경될 코드
 }
```
#### 함수전달

```
setState((prevState, props) => {
    return {
      item: prevState.item + 1
    };
```
첫번째 인수: 이전의state
두번째 인수: props
