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

  # Access Token + Refresh Token을 이용한 인증
  ![image](https://github.com/mini-aron/IL/assets/105274015/43ca4ed4-a77d-426f-a8ad-48045552beeb)

  # OAuth 2.0을 이용한 인증

  ![image](https://github.com/mini-aron/IL/assets/105274015/52ad46f8-864b-441b-ac9c-3010d29adc46)
