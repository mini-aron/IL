# 세션과 쿠키를 이용한 인증
![image](https://github.com/mini-aron/IL/assets/105274015/95b715b7-5429-47f3-aff7-ac521a7318df)
+ 사용자가 로그인을 요청
+ 서버에서 계정정보를 읽어 확인후 사용자에게 고유한 ID값을 부여해 세션저장소에 저장한 후, 이와 연결되는 Session ID 발급
+ 서버는 HTTP응답 헤더에 발급된 Session ID를 실어 보냄. 이후 매 요청마다 HTTP요청헤더에 Session ID가 담긴 쿠키를 실어 보낸다.
+ 서버에서는 쿠키를 받아 세션저장소에서 대조후 대응되는 정보를 가져옴
+ 인증이 완료되고 서버는 사용자에 맞는 데이터를 전송

# Access Token을 이용한 인증

![image](https://github.com/mini-aron/IL/assets/105274015/8b7f70e2-716a-4e59-b2e6-593ba5ce216f)
+ 사용자가 로그인을 요청
+ 서버에서 계정 정보를 읽어 사용자를 확인 후 , 사용자의 고유한 ID값을 부여하고 Payload에 정보를 넣는다.
+ JWT 토큰의 유효시산을 설정한다.
+ SECRET KEY를 통해 암호화된 Access Token을 HTTP 응답 헤더에 실어 보낸다.
+ 사용자는 Access Token을 받아 저장후, 인증이 필요한 요청마다 토큰을 HTTP 요청 헤더에 실어 보낸다.
+ 서버에서 해당 토큰의 Verify Signature를 SECRET KEY로 복호화한 후, 조작 여부, 유효기간을 확인한다.
+ 검증이 완료되면 payload를 디코딩해 사용자의 ID에 맞는 데이터를 가져온다.
+ 
# Access Token + Refresh Token을 이용한 인증
![image](https://github.com/mini-aron/IL/assets/105274015/43ca4ed4-a77d-426f-a8ad-48045552beeb)
+ 사용자가 로그인을 요청한다.
+ 서버에서 회원DB와 값을 비교한다.
+ 로그인이 완료되면 Access Token, Refresh Token을 발급해 HTTP 응답 헤더에 실어 보낸다. (이때 일반적으로 DB에 Refresh token을 저장해둔다.)
+ 사용자는 Refresh Token은 안정한 저장소에 저장 후, Access Token을 HTTP요청 해더에 실어 요청을 보낸다.
+ Access Token을 검증해 맞는 데이터를 보낸다.
+ 시간이 지나 Access Token이 만료된후
+ 사용자는 이전과 동일하게 Access Token을 HTTP요청 헤더에 실어 보낸다.
+ 서버는 Access Token이 만료됨을 확인하고 권한 없음을 신호로 보낸다.
+ 사용자는 Refresh Token과Access token을 실어 보낸다.
+ 서버는  받은 Access Token이 조작되지 않았는지 확인한 후, HTTP 요청 헤더의 Refresh Token과 사용자의 DB에 저장되어 있던 Refresh Token을 비교한다.Token이 동일하고 유효기간도 지나지 않았다면 새로운 Access Token을 발급해준다.
+ 서버는 새로운 Access Token을 실어 다시 요청을 진행한다.



# OAuth 2.0을 이용한 인증

+ Resource Owner : 일반 사용자

+ Client : 우리가 만든 웹 어플리케이션

+ Authorization Server : 권한 관리 및 Access Token, Refresh Token을 발급해주는 서버

+ Resource Server : OAuth 2.0을 관리하는 서버의 자원을 관리하는 곳
![image](https://github.com/mini-aron/IL/assets/105274015/52ad46f8-864b-441b-ac9c-3010d29adc46)

