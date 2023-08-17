## router
라우터 객체에 대한 정보를 알 수 있다.
### 사용법
```js
import { useRouter } from 'next/router'

function App(){
    const router = useRouter();
}
```
### router object

+ #### 1. asPath
    - basePath나 locale가 포함되지않은 path
+ #### 2. basePath
    - 활성화 되어있는 basePath
+ #### 3. isFallback
    - fallback 에 관련된 값(boolen) 또는 'blocking'으로 들어옴
        + 빌드타임에 생성해놓지 않은 path로 요청이 들어온 경우 어떻게 할지 정하는 부분
+ #### 4. isReady
    - 라우터 필드가 클라이언트 측에서 업데이트 되거 사용할 준비가 되었는지 여부
        + use Effect메소드 내에서만 사용해야하며 서버에서 조건부로 렌더링 하는 데에 사용해야한다.
+ #### 5. isPreview
    - 현재 미리보기 모드인지 여부
+ #### 6. pathname
    - 활성화 되어 있는 basePath
        + next.config.js에 지정된 경로 접두사
+ #### 7. query
    - 현재 router 값
        + pages폴더 하위에 있는 페이지 경로

### router.push | router.replace
클라이언트에서 페이지 전황을 위해 사용
push로 이동시 history stack에 쌓여서 뒤로가기가 가능하고,
replace로 이동시 history stack에 쌓이지 않아 뒤로가기가 불가능 하다.
```js
router.push(url,as,options) 
router.replace(url,as,options)
```
#### 1. url
- 이동할 url - url객체 사용가능
#### 2. as
- 이동후 브라우저에 표시될 URL
#### 3. options
- scroll: `default: true`탐색후 페이지 맨 위로 스크롤 제어
- shallow: `default: false`  
            -> getStaticProps, getServerSideProps, getInitialProps를 다시 실행하지 않고 현재 페이지 경로 업데이트
- locale: 새로운 페이지의 locale

### router.prefetch
빠른 클라이언트 전환을 위해 페이지를 데이터를 미리 가져온다.
* next/link는 자동으로 페이지를 미리 가져오기 때문에 next/link가 없는 탐색에 유용하다.
```js
router.perfetch(url,as)
```
#### 1. url
- 이동할 url
#### 2. as
- 이동후 브라우저에 표시될 URL

### router.beforePopState
라우터가 동작하기전 어떤 작업을 하고싶을 때 사용
-popstate: 사용자의 세션기록 탐색으로 인해 현재 활성화된 기록 항목이 바뀔 때 발생

### router.back
뒤로가기 버튼 클릭과 같음
 window.history.back()  실행
```js
import { useRouter } from 'next/router';
export default function 'App(){
    const router = useRouter();

    return (
        <button type="button" onClick={() => router.back()}>
      Click here to go back
    </button>
    );
}
```

### router.reload
새로고침 버튼 클릭과 같음  
 window.history.reload()  실행



