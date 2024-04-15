# Route-based code spliting(라우터 기반 코드 스플릿팅)
적용하기 좋은 곳은 route이다.  
웹페이지 로드시간의 대부분은 페이지 전환에서 발생하며, 페이지를 한번에 렌더링 하는게 대부분이기 때문에 렌더링 중간에 사용자가 페이지와 상호작용할 가능성은 거의 없다.

```js
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
import React, { Suspense, lazy } from 'react';

const Home = lazy(() => import('./routes/Home'));
const About = lazy(() => import('./routes/About'));

const App = () => (
  <Router>
    <Suspense fallback={<div>Loading...</div>}>
      <Switch>
        <Route exact path="/" component={Home}/>
        <Route path="/about" component={About}/>
      </Switch>
    </Suspense>
  </Router>
);
```