
## rootReducer
> createStore함수를 사용하여 store를 생성할 때 리듀서는 하나만 사용해야한다.  
> 만약 리듀서가 여러개라면 rootReducer파일을 만들고 combineReducers함수를 사용하여 기존의 리듀서들을 하나로 합칠 수 있다.
```javascript
// src/modules/index.js

import { combineReducers } from "redux";
import counter from "./counter";

const rootReducer = combineReducers({
    counter,
})

export default rootReducer;
```