# NEXT.js
## NEXT.js란?
+ nextjs는 React를 위해 만들어진 `오픈소스 자바스크립트 웹 프레임워크`다.
+ 서버사이드 렌더링(SSR), 정적 사이트 생성(SSG), 충분 정적 재생성(ISR)과 같은 기능을 제공한다. 

## NEXT.js가 제공하는 주요 기능
+ `hot reloading` : 개발중 저장되는 코드는 자동으로 새로고침된다.
+ `automatic routing` : pages폴더에 있는 파일은 해당 파일 이름으로 라우팅된다.(pages/page1.tsx => localhost:3000/page1)public폴더도 pages폴더와 동일하게 라우팅 가능하다.(모든사람이 페이지에 접근할 수 있으므로 지양)
+ `single file components` : `style hsx`를 사용함으로 컴포넌트 내부에 해당 컴포넌트만 스코프를 가지는 css를 만들 수 있다.
+ `server landing` : 클라이언트 렌더링과 다르게 서버렝더링을 한 페이지의 소스보기를 클릭하면 내부에 소스가 있다.
+ `code splitting` : dynamic import를 이용하면 손쉽게 코드 스플리팅이 가능하다. 코드 스플리팅은 내가 원하는 페이지에서 원하는 자바스크립트와 라이브러리를 렌더링 하는것이다. 모든번들(chunk.sj)이 하나로 묶이지 않고, 각각 나뉘어 효율적으로 로딩시간을 개선할 수 있다.
+ `typescript` : 타입스크립트를 설치하고(yarn add typescript @types/node @types/react) 명령어 (yarn run dev)만 하면 자동으로 tsconfig, next-end.d.ts가 생성되어 타입스크립트로 코딩이 가능해진다.
+ `_document.tsx` : meta 태그를 정의하거나, 전체페이지에 관여하는 컴포넌트.
    - 여기의 console은 서버에서만 보이고 클라이언트에서는 안보인다.
    - render요소는 반영하지만 페이지구성요소만 반영되고 js는 반영하지 않기때문에 componentDidMount같은 훅도 실행 되지 않는다.(정말 static한 상황에만 사용)
+ `_app.tsx` : 이곳에서 렌더링하는 값은 모든 페이지에 영향을 준다.
    - 최초로 실행되는것은 `_app.tsx`
    - _app.tsx`은 클라이언트에서 띄우길 바라는 전체 컴포넌트 -> 공통 레이아웃임으로 최초실행되며 내부에 컴포넌트들을 실행한다.
    - 내부에 컴포넌트가 있다면 전부 실행하고 html의 body로 구성한다.
    - Component,pageProps를 받는다.
+ `sass 사용` : 따로 config파일을 정의하지않고 css파일을scss로 바꾸고 `yarn add sass --dev`를 해주면 next에서 알아서 설정해준다.
+ `Link 사용` : a 태그는 전혀 다른 사이트로 페이지를 이동시켜 다시 돌아오지 않는 경우만 사용하고, 그 이외에는 모두 Link 태그를 사용한다.
+ `동적 url(dynamic route)` : 가변적으로 변하는 url에 대해 동적 url을 지원한다. [] 문법으로 동적 페이지를 생성하는 동적 url을 만들 수 있다.
+ `글로벌 스타일 정의 가능` : _app.tsx에서만 정의가 가능. 다른컴포넌트에 정의한경우 다른 클래스와 겹쳐 오류를 발생할 수 있다.

### 장점
+ 검색 엔진 최적화를 위한 SSR(Server Side Rendering) 기능이 내장