## Application Service > RTCS > Error Code
### 접속 권한 요청
RTCS에 접속하기 위한 접속 권한을 요청합니다. 제공 받은 URL을 이용하여 클라이언트에서 접속하면 됩니다..

[URL]

```
POST /v2/auth/{appkey}/access
```

[Http status code]

|code| 구분 | 코드명 | 설명 |
|---|---|---|---|
|400| 에러 |Bad Request | 잘못된 요청일 경우 발생한다.|
|401| 에러 |Unauthorized | 인증 실패일 경우 발생한다.|
|413| 에러 |Request Entity Too Large | 메시지 크기가 지정된 크기보다 더 큰 경우 발생한다.|
|500| 에러 |Server Error | 서버가 점검 중이거나 장애인 경우 발생한다.|
|503| 에러 |Server Maintenance | 서버가 점검 중인 경우 발생한다.|


### 채널 메시지 전달 요청
채널에 가입된 클라이언트 들에게 메세지를 전달합니다
* 주의)
  * 메세지의 크기는 **1mb** 보다 작아야합니다.
  * 큰메세지를 보낼 경우 **413** 에러가 발생합니다..
* 메세지 크기만 잘 조절하면 base64를 이용해 바이너리도 전달 가능 합니다.

[URL]

```
POST /v2/event/{appkey}/channel
```

[Http status code]

|code| 구분 | 코드명 | 설명 |
|---|---|---|---|
|400| 에러 |Bad Request | 잘못된 요청일 경우 발생한다.|
|401| 에러 |Unauthorized | 인증 실패일 경우 발생한다.|
|413| 에러 |Request Entity Too Large | 메시지 크기가 지정된 크기보다 더 큰 경우 발생한다.|
|500| 에러 |Server Error | 서버가 점검 중이거나 장애인 경우 발생한다.|
|503| 에러 |Server Maintenance | 서버가 점검 중인 경우 발생한다.|

### 채널 존재 여부 확인
채널이 존재 하는지 확인 할 수 있습니다.

[URL]

```
GET /exists/{appkey}
```

[Http status code]

|code| 구분 | 코드명 | 설명 |
|---|---|---|---|
|400| 에러 |Bad Request | 잘못된 요청일 경우 발생한다.|
|401| 에러 |Unauthorized | 인증 실패일 경우 발생한다.|
|500| 에러 |Server Error | 서버가 점검 중이거나 장애인 경우 발생한다.|
|503| 에러 |Server Maintenance | 서버가 점검 중인 경우 발생한다.|

### 채널에 가입된 세션 정보 조회
채널에 가입된 세션의 목록을 조회합니다. 조회가 가능한 채널은 **presence** 와 **member** 채널입니다.

[URL]

```
GET /v2/channel/{appkey}/sessions?channel={channel_name}
```

[Http status code]

|code| 구분 | 코드명 | 설명 |
|---|---|---|---|
|400| 에러 |Bad Request | 잘못된 요청일 경우 발생한다.|
|401| 에러 |Unauthorized | 인증 실패일 경우 발생한다.|
|500| 에러 |Server Error | 서버가 점검 중이거나 장애인 경우 발생한다.|
|503| 에러 |Server Maintenance | 서버가 점검 중인 경우 발생한다.|

### 채널에 가입된 세션 개수 조회
채널에 가입된 세션의 갯수를 조회 할 수 있습니다.. 조회가 가능한 채널은 **presence** 와 **member** 채널입니다.

[URL]

```
GET /v2/channel/{appkey}/count?channel={channel_name}
```

[Http status code]

|code| 구분 | 코드명 | 설명 |
|---|---|---|---|
|400| 에러 |Bad Request | 잘못된 요청일 경우 발생한다.|
|401| 에러 |Unauthorized | 인증 실패일 경우 발생한다.|
|500| 에러 |Server Error | 서버가 점검 중이거나 장애인 경우 발생한다.|
|503| 에러 |Server Maintenance | 서버가 점검 중인 경우 발생한다.|
