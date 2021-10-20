### 필요 이유
- Connectionless
- Stateless (HTTP 통신 - `요청 & 응답` 후에 접속이 끊기면 클라이언트의 상태 정보를 알 수 없다.)

#### 상태를 유지하기 위한 방법 - `쿠키와 세션`

### 쿠키
`Key-Value` 쌍의 작은 데이터 파일
- 구성요소 (쿠키이름, 쿠키값, 만료시간, 전송할 도메인명, 전송할 경로, 보안연결여부, HttpOnly여부)
- Set-Cookie 이용해 설정

### 세션
브라우저가 종료되기 전까지 클라이언트의 요청을 유지하게 해주는 기술

# 차이점
- 저장위치 (쿠키 - 로컬, 세션 - 로컬 & 서버)
- 보안 (쿠키 - 탈취 및 변조 가능, 세션 - ID 값으로 서버에도 저장되어 상대적으로 안전)
- Lifecycle (쿠키 - 파일로 남지만, 세션 - 종료 시 세션 삭제)
- 속도 (쿠키 - 파일에서 읽기 때문에 빠름, 세션 - 서버에서 처리해야하기 때문에 비교적 느림)


### 주의사항
- Session -> `Login & Logout` 관련 저장, 삭제 시 redirect할 시 문제 발생하는 경우가 있음

session-file-store 사용 시 해결 방법 -> `req.session.save & req.session.destroy 사용`

[Session 코드 참고](https://github.com/kdh-92/lecture/blob/main/opentutorials/session/router/auth.js)

이유 : 세션이 변경되고 file에 적용되는 중에 redirect가 이뤄지며 정확한 동작이 되지 않는다.

### 세션 + Passport
[생활코딩 & Passport](https://opentutorials.org/module/3655)

- 로그인 확인 및 로그아웃 관련 문제 발생

=> FileStore 파일 쓰기 작동 방식이 Windows와 Unix(Linux) 방식과 달라 작동이 다르게 적용됨.
`connect-loki` 사용 시 디렉토리 루트에 session-store-db 파일을 만들어 passport 관련 사용자 정보를 확인할 수 있다.