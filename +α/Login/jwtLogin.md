# access token과 refresh token을 이용한 login

## 시나리오
1. RefreshToken 유효 + AccessToken 유효
  => 정상적으로 로그인이 유지되는 경우.
  
2. RefreshToken 유효 + AccessToken 만료
  => AccessToken이 만료되었지만 RefreshToken이 유효하기 때문에 
     RefreshToken을 사용해 AccessToken을 발급받을 수 있음.
  
3. RefreshToken 만료 + AccessToken 유효
  => AccessToken이 만료될 때까지 AccessToken을 사용할 수 있음. 
     하지만 만료 기간이 짧기 때문에 이후 로그인이 필요함.
  
4. RefreshToken 만료 + AccessToken 만료
  => 로그인이 필요한 경우.

## 발급방법
1. api요청후 만료되었다면 재발급
  => access Token만료 경우에 대해 에러처리 및 이 과정이 모든 api요청에 들어가야한다는 점이 있음
2. 주기적으로 토큰발급
   => 주기적으로 api요청이 발생하며 유효기간이 남았을떄도 access Token을 발급받기때문에 낭비가 발생한다.

### Access Token 재발급 방법
보통 로그인 성공시 발행되며 저장소에 저장된다. 
그리고 로그아웃을 하면 저장소에서 Refresh Token을 삭제하여 사용이 불가능하도록 한다.

### 재발급 과정
1. Refresh Token 유효성 체크
2. 저장소에 Refresh Token 존재유무 체크
3. 1, 2 모두 검증되면 재발급 진행
4. Response header에 새로 발급한 Access Token 저장