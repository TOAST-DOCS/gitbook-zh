## Data & Analytics > Log & Crash Search > API Guide

HTTP 프로토콜을 사용해서 Log & Crash 수집 서버에 로그를 전송할수 있습니다. 

> - JSON/HTTP로 Log & Crash 수집 서버에 로그를 전송할 때는 다음 주소를 사용해야 합니다.
>     - Log & Crash: api-logncrash.cloud.toast.com
>     - Method of Delivery: POST
>     - URI: /v2/log
>     - Content-Type: "application/json"
> - 로그를 전송하기 전에 Log & Crash에 프로젝트를 등록했는지 확인합니다.  
> - "logTime"은 Log & Crash 시스템에서 사용합니다. 해당 키를 사용하면 Log & Crash에서는 무시합니다.  
> -  키 이름에 공백 문자가 들어가지 않게 주의합니다. 예를 들어 "UserID"와 "UserID "는 서로 다른 키로 인식됩니다. 
> -  HTTP 요청 하나의 최대 크기는 52MB입니다.
> -  로그(JSON) 하나의 최대 크기는 8MB(8388608바이트)입니다.

아래와 같은 JSON 형식을 사용합니다.

```
{
	"projectName": "__Appkey__",
	"projectVersion": "1.0.0",
	"logVersion": "v2",
	"body": "This log message come from HTTP client.",
	"logSource": "http",
	"logType": "nelo2-log",
	"host": "localhost"
}
```

[Default Parameters]

```
Log Search를 위한 파라미터

projectName: string, required
	[in] Appkey

projectVersion: string, required
	[in] 버전. 사용자 지정 가능. "A~Z, a~z, 0~9,-._"만 포함.

body: string, optional
	[in] Log messages.

logVersion: string, required
	[in] Log format version. "v2".

logSource: string, optional
	[in] 로그 소스. Log Search에서 필터링을 위해 사용. 정의되지 않으면 "http".

logType: string, optional
	[in] 로그 타입. Log Search에서 필터링을 위해 사용. 정의되지 않으면 "log".

host: string, optional
	[in] 로그를 보내는 단말의 주소. 정의되지 않으면 수집 서버에서 peer-address를 사용해 자동으로 채움.
```

[Other Parameters]

```
sendTime; string, optional
	[in] 단말이 보낸 시간. 입력 시 Unix timestamp로 입력.

logLevel; string, optional
	[in] Syslog 이벤트용.

UserBinaryData; string, optional
	[in] Display [Download|Show] link on the log search screen, and send with values encoded with base64.

UserTxtData; string, optional
	[in] 로그 검색 화면에서 [다운로드|보기] 링크 표시, base64 인코딩된 값을 담아 전송.

txt*; string, optional
	[in] 필드 이름이 txt로 시작하는 필드(txtMessage, txt_description 등)는 text 필드로 저장. 로그 검색 화면에서 필드값의 일부 문자열로 검색(full text search) 가능. 필드의 크기는 1MB로 제한됨.

long*; long, optional
    [in] 필드 이름이 long으로 시작하는 필드(longElapsedTime, long_elapsed_time 등)는 long 타입 필드로 저장됨. 로그 검색 화면에서 long 타입 range 검색 가능.

double*; double, optional
    [in] 필드 이름이 double로 시작하는 필드(doubleAvgScore, double_avg_score 등)는 double 타입 필드로 저장됨. 로그 검색 화면에서 double 타입 range 검색 가능.
```

[Custom Fields]

```
커스텀 필드 이름은 "A-Z, a-z"로 시작하고 "A-Z, a-z, 0-9, -, _" 문자를 사용할 수 있습니다.

위의 기본 파라미터, Crash 파라미터와 이름이 중복되면 안 됩니다.

커스텀 필드는 필드 전체 문자열과 일치하는 검색만 가능합니다(exact match).

커스텀 필드의 길이는 1KB로 제한됩니다. 1KB 이상 전송하거나, 필드값의 일부 문자열을 검색해야 할 때는 txt* prefix를 붙여 필드를 생성해야 합니다.
```

[Return Value]
수집 서버에서 다음과 같이 반환합니다.

```
Content-Type: application/json

{
	"header":{
		"isSuccessful":true,
		"resultCode":0,
		"resultMessage":"Success"
	}
}

isSuccessful: boolean
	[out] 성공 시 true, 실패 시 false

resultCode: int
	[out] 성공 시 0, 실패 시 오류 코드

resultMessage: string
	[out] 성공 시 "Success", 실패 시 오류 메시지
```

[Bulk Delivery]
Bulk로 전송하려면 JSON array 형태로 전송합니다.

```
[
    {
        "projectName": "__Appkey__",
        "projectVersion": "1.0.0",
        "logVersion": "v2",
        "body": "This log message come from HTTP client. (1/2)",
        "logSource": "http",
        "logType": "nelo2-log",
        "host": "localhost"
    },
    {
        "projectName": "__Appkey__",
        "projectVersion": "1.0.0",
        "logVersion": "v2",
        "body": "This log message come from HTTP client. (2/2)",
        "logSource": "http",
        "logType": "nelo2-log",
        "host": "localhost"
    }
]
```

* 참고
    * 웹에서는 수신 시간 기준으로 로그를 정렬해 표시하는데, Bulk 전송의 경우 동일한 시간에 수신한 것으로 간주되어 사용자가 전송한 순서가 유지되지 않습니다.
        * Bulk로 전송하는 로그들의 순서를 유지하려면 각 로그에 lncBulkIndex 필드를 추가해 Integer값을 지정한 후 전송하면 서버에서는 이 값을 기준으로 내림차순으로 표시합니다.

```
[
    {
        "projectName": "__Appkey__",
        "projectVersion": "1.0.0",
        "logVersion": "v2",
        "body": "first message",
        "logSource": "http",
        "logType": "nelo2-log",
        "host": "localhost",
        "lncBulkIndex":1
    },
    {
        "projectName": "__Appkey__",
        "projectVersion": "1.0.0",
        "logVersion": "v2",
        "body": "second message",
        "logSource": "http",
        "logType": "nelo2-log",
        "host": "localhost",
        "lncBulkIndex":2
    }
]
```
	* 위 예시와 같이 전송한 경우 서버에서는 second message -> first message 순서로 표시합니다.

수집 서버에서는 전송된 순서에 따라 각각의 결괏값을 JSON array 형태로 다시 반환합니다.

```
Content-Type: application/json

{
    "header":{
        "isSuccessful":true,
        "resultCode":0,
        "resultMessage":"Success"
    },
    "body":{
        "data":{
            "total":5,
            "errors":2,
            "resultList":[
                {"isSuccessful":true, "resultMessage":"Success"},
                {"isSuccessful":true, "resultMessage":"Success"},
                {"isSuccessful":false, "resultMessage":"LogVersion Mismatch: v1, /v2/log"},
                {"isSuccessful":false, "resultMessage":"The project(invalidProject) is not registered"},
                {"isSuccessful":true, "resultMessage":"Success"}
            ]}
        }
    }
}

total: int
    [out] Total number of delivered logs

errors: int
    [out] Number of errors in delivered logs

resultList: array
    [out] Result value of each delivered log
```

## Samples

[curl을 사용해 정상적으로 로그를 전송한 경우]

```
//POST 메서드을 사용해 로그 전송
$ curl -H "content-type:application/json" -XPOST 'https://api-logncrash.cloud.toast.com/v2/log' -d '{
	"projectName": "__Appkey__",
	"projectVersion": "1.0.0",
	"logVersion": "v2",
	"body": "this log message come from http client, and it is a simple sample.",
	"logSource": "http",
	"logType": "nelo2-http"
}'
```

[로그 전송에 실패하는 경우]

```
//When URL is incorrect (log -> loggg)
$ curl -v -H 'content-type:application/json' -XPOST "api-logncrash.cloud.toast.com/v2/loggg" -d '{
	"projectName": "__Appkey__",
	"projectVersion": "1.0.0",
	"logVersion": "v2",
	"body": "this log message come from http client, and it is a simple sample.",
	"logSource": "http",
	"logType": "nelo2-http"
}'


//When a wrong field key (_xxx) is used
$ curl -v -H 'content-type:application/json' -XPOST "api-logncrash.cloud.toast.com/v2/log" -d '{
	"projectName": "__Appkey__",
	"projectVersion": "1.0.0",
	"logVersion": "v2",
	"body": "this log message come from http client, and it is a simple sample.",
	"logSource": "http",
	"logType": "nelo2-http",
	"_xxx": "this is a invalid key"
	}'
커스텀 키는 "A~Z, a~z, 0~9, -_"를 포함하고 알파벳으로 시작해야 합니다.
커스텀 키는 "A~Z, a~z, 0~9, -_"를 포함하고 알파벳으로 시작해야 합니다.
```

[Bulk log delivery using curl]

```
//POST 메서드을 사용해 로그 전송
$ curl -H "content-type:application/json" -XPOST 'https://api-logncrash.cloud.toast.com/v2/log' -d '[
    {
        "projectName": "__Appkey__",
        "projectVersion": "1.0.0",
        "logVersion": "v2",
        "body": "This log message come from HTTP client, and it is a simple bulk sample. (1/2)",
        "logSource": "http",
        "logType": "nelo2-log"
    },
    {
        "projectName": "__Appkey__",
        "projectVersion": "1.0.0",
        "logVersion": "v2",
        "body": "This log message come from HTTP client, and it is a simple bulk sample. (2/2)",
        "logSource": "http",
        "logType": "nelo2-log"
    }
]'
```
