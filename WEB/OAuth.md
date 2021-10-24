# OAuth
> 다양한 플랫폼 환경에서 권한 부여를 위한 산업 프로토콜

`인증` - 시스텝 접근을 확인하는 것 (openID)
`권한` - 행위의 권리를 검증하는 것

Client (third party Applicaion)에 로그인 정보를 가지는 대신 AccessToken을 이용

[ 용어 ]
- Resource Server
    - 제어하고자 하는 자원을 보유하는 서버
- Resource Owner
    - 서비스를 통해 로그인하는 실제 유저
- Client
    - Resource Server에 접속해서 정보나 자원을 가져와 사용하고 하는 웹 어플리케이션

# OAuth Flow
- Client 등록
    - Client -> Resource Server 이용하기 위해 자신의 서비스 등록
        - Client ID - 웹 어플리케이션 구별할 식별키
        - Client Secret - Client ID 대한 비밀키
        - Authorized redirecttt URL (Authorization Code 전달 받을 주소)
- Resourece Owner 승인
    - Resource Owner - Resource Server에 접속하여 로그인 수행
    - 파라미터 통해 Clientt 검사
        - ClientID 검사
        - 해당 ClientID 해당하는 Redirect URL이 같은지 검사
    - 검증이 마무리 되면 Resource Server는 Resource Owner에게 scope에 해당하는 권한을 Client에 부여할건지 물어본다.
```
ex) github OAuth Login url
GET https://github.com/login/oauth/authorize?client_id={client_id}&redirect_uri={redirect_uri}?scope={scope}
```
- Resource Server 승인
    - Redirect URL로 클라이언트 리다이렉트 (Client에게 Access Token 발급 전에 임시 암호 `Authorization Code` 발급)
    - Client에서 ClientID, Client Secret, Code를 Resource Server에 전달 후 유효한 요청이면 `Access Token` 발급
    - Client는 해당 토큰을 서버에 저장한 후 API 호출 시 헤더에 `Access Token`을 담아 보낸다.

## Refresh Token
- Access Token 만료 기간이 있어, Client에 Refresh Token을 함게 발급해서 만료된 경우 `Refresh Token`을 이용해 새로운 Access Token 을 발급 받아 사용자가 다시 로그인 하지 않아도 된다.