## Dooray! > Messenger > Incoming Hook Guide

### 인커밍 훅

Dooray!에서는 특정 대화방으로 메시지를 전송할 수 있는 인커밍 훅(incoming hook)을 제공합니다.

### 대화방에 메시지 전송하기

터미널 환경에서 다음과 같은 스크립트를 작성합니다. Linux, macOS 기준이고, `curl`이 설치되어 있다고 가정합니다.

```bash
hook_url=
curl -H "Content-Type: application/json" -X POST -d '{"botName": "MyBot", "botIconImage": "https://static.dooray.com/static_images/dooray-bot.png", "text":"Dooray!"}' $hook_url
```

위 스크립트에서 `hook_url`에 특정 대화방을 지칭할 URL을 적어야 합니다. 

'설정' 메뉴에서 '서비스 연동'을 선택하고 '서비스 추가' 탭에서 'incoming'의 '연동 추가' 버튼을 누릅니다. 화면에서 연동하고 싶은 대화방을 체크하고 '저장' 버튼을 누르면 해당 주소가 클립보드에 복사됩니다.

그 주소를 위 스크립트에서 `hook_url` 다음에 붙입니다.

```bash
hook_url=https://hook.dooray.com/services/...
curl -H "Content-Type: application/json" -X POST -d '{"botName": "MyBot", "botIconImage": "https://static.dooray.com/static_images/dooray-bot.png", "text":"Dooray!"}' $hook_url
```

이 내용을 `simple.sh`라고 저장하고 명령행에서 실행하면 대화방에 메시지가 전송되는 것을 확인할 수 있습니다.


![hook1](http://static.toastoven.net/prod_dooray_messenger/hook1.png)


### 데이터 포맷

앞서 실행한 프로그램에서 JSON 부분만 보면 다음과 같습니다.

```json
{
    "botName": "MyBot", 
    "botIconImage": "https://static.dooray.com/static_images/dooray-bot.png", 
    "text":"Dooray!"
}
```

`text` 영역 이외에 `attachments` 영역을 이용하면 본문 외에 제목을 추가할 수 있고, 색이 있는 사각형으로 감쌀 수도 있습니다. 

```json
{
    "botName": "MyBot", 
    "botIconImage": "https://static.dooray.com/static_images/dooray-bot.png", 
    "text":"Dooray!",
    "attachments" : [
        {
            "title" : "title",
            "titleLink" : "http://dooray.com/",
            "text" : "message",
            "color" : "red"
        }
    ]
}
```

이 내용을 전송하면 다음 같이 나오게 됩니다. 위의 내용을 `simple.sh`로 옮길 때 줄바꿈을 없애야 합니다.

![hook2](http://static.toastoven.net/prod_dooray_messenger/hook2.png)


필요하다면 `attachments` 영역은 여러 번 반복 할 수 있습니다.

```json
{
    "botName": "MyBot", 
    "botIconImage": "https://static.dooray.com/static_images/dooray-bot.png", 
    "text":"Dooray!",
    "attachments" : [
        {
            "title" : "title",
            "titleLink" : "http://dooray.com/",
            "text" : "message",
            "color" : "red"
        },
        {
            "title" : "title2",
            "titleLink" : "http://dooray.com/",
            "text" : "message2",
            "color" : "green"
        }
    ]
}
```

![hook3](http://static.toastoven.net/prod_dooray_messenger/hook3.png)
