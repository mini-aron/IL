# MSW(Mock Service Worker)
> Service Worker를 이용해 서버를 향한 실제 네트워크 요청을 가로채 모의 응답(Mocked response)를 보내주는 API Mocking 라이브러리다.  
> 직접 Mock서버를 구현하지 않아도, 네트워크 수준에서 API를 Moking 할 수 있다.  

## Service Worker
MSW가 이런 기능들을 제공할 수 있는 이유는 Service Worker를 통해 HTTP 요청을 가로채기 때문이다.

MDN 문서에선 Service Worker를 아래와 같이 정의하고 있다.
> service worker는 웹 응용 프로그램, 브라우저, 그리고 (사용가능한 경우) 네트워크 사이의 프록시 역할을 합니다.  
> service worker의 개발의도는 여러가지가 있지만, 그중에서도 효과적인 오프라인 경험을 생성하고, 네트워크 요청을 가로채서 네트워크 사용가능 여부에 따라 적절한 행동을 취하고, 서버의 자산을 업데이트 할 수 있습니다. 또한 푸시 알림과 백그라운드의 동기화 API로의 접근도 제공합니다.

Service Worker는 브라우저가 백그라운드에서 실행하는 스크립트로, 애플리케이션의 UI블록 없이 연산을 처리할 수 있다.
(웹 애플리케이션의 메인 스레드와 분리된 별도의 백그라운드 스레드에서 실행됨)
Service Worker는 웹서비스와 브라우저 및 네트워크 사이에서 프록시 역할을 하고 오프라인에서도 사용할 수 있도록 한다. 또한 Service worker의 라이프사이클은 웹페이지와 완전히 별개이다.  
  
단, Service Worker는 IE와 같은 일부 브라우저에서 지원이 되지 않으며, HTTPS 보안 프로토콜 환경이 필요하다. (localhost 환경 제외). 네트워크 중간에서 연결을 가로채고 조작하는 기능 때문에 반드시 HTTPS가 제공되어야 한다.
  
MSW는 Service Worker 덕분에 다른 라이브러리에 종속되지 않고 호환성 문제 없이 모의 API를 작동시킨다.
## MSW 작동 방식
MSW 라이브러리를 설치하면 브라우저에 Service Worker을 등록한다.  
이후 브라우저에서 이뤄지는 네트워크 요청들을 Service Worker가 가로채게 된다.  
Service Worker는 가로챈 요청을 복사해 실제 내트워크가 아닌 클라이언트 사이드에 있는 MSW 라이브러리로 보낸 후, 등록된 핸들러를 통해 모의응답(Mocked response)을 제공받는다.  
마지막으로 제공받은 모의 응답(Mocked response)을 브라우저에 그대로 전달하게 된다.  
  
이를 통해, 실제 서버와 직접적인 연결 없이 보내는 요청에 대한 응답을 Mocking 할 수 있게된다.  

![](https://velog.velcdn.com/images/khy226/post/49ca8fe5-ce19-4c98-b4eb-14f70b53410b/image.png)
Mock Service Worker 다이어그램(출저:[https://mswjs.io/docs/#request-flow-diagram](https://mswjs.io/docs/#request-flow-diagram))  
```
1. 브라우저가 Service Worker에 요청을 보냄
2. Service Worker가 해당 요청을 가로채서 복사함
3. 서버에 요청을 보내지 않고, MSW 라이브러리의 핸들러와 매칭시킴
4. MSW가 등록된 핸들러에서 모의 응답 (mocked response)를 Service Worker에게 전달함
5. 마지막으로, Service Worker가 모의 응답을 브라우저에게 전달함
```
