## Application Service > RTCS > Console Guide

## 서비스 신청 방법
* 서비스 활성 버튼을 클릭하면 위와 같은 화면이 나옵니다.
* 서비스 활성화 한뒤 Setting 화면에서 프로젝트를 설정을 할 수 있습니다..

## 서비스 대쉬보드
* 서비스의 사용자수와 사용량을 모니터링 할 수 있습니다.

![dashboard](http://static.toastoven.net/prod_rtcs/dashboard.png)

## 서비스 대쉬보드
* 메세지를 주고 받으면서 테스트가 가능합니다.

![message](http://static.toastoven.net/prod_rtcs/message.png)

## 서비스 대쉬보드
* API Server를 통해서 멤버채널과 출석채널을 구독중인 세션 목록과 개수를 확인할 수 있습니다.

![session](http://static.toastoven.net/prod_rtcs/session.png)


## 서비스 설정
* 서비스의 설정을 할 수 있습니다.

### 서비스 설정에 필요한 자료
- SSL 사용 여부 : https, wss 를 사용해야할 때 체크
- WebAuth URL : 채널 가입시에 서비스 서버에 인증 확인을 요청하는 URL. Web Auth는 HTTP/HTTPS POST 요청으로 전달되고, 내용(body)는 JSON 형태이다.
- Hook URL : 아래 이벤트에 대한 hook을 받고 싶을 때 체크
- 전달 받을 hook event
  - 연결 완료 : 클라이언트가 접속을 하면 전달됨
  - 연결 종료 : 연결이 종료 되면 전달됨
  - 채널 가입 : 채널에 가입을 하면 전달 됨
  - 채널 탈퇴 : 채널에 탈퇴를 하면 전달 됨

![setting](http://static.toastoven.net/prod_rtcs/n-setting.png)
