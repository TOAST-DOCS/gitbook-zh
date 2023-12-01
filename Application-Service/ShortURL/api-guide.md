## Application Service > ShortURL > API Guide

### Basic information
```http
API Endpoint: https://api-shorturl.nhncloudservice.com
```

## Shortened URL

### 1. Create
- Create a shortened URL.

[URL]

```http
POST /open-api/v1.0/appkeys/{appKey}/urls
Content-Type: application/json
```

#### Request

[Path Variables]

| Name | Type | Required | Description |
|---|---|---|---|
| appKey | String | O | Service Appkey (Can be found on the **Manage Service** tab) |

[Request Body]

| Name | Type | Required | Description |
|---|---|---|---|
| url | String | O | Full URL |
| domain | String | X | The domain to use for shortened URL (created as nh.nu if not specified) |
| backHalf | String | X | Shortened URL ID (Refers to `example` in https://nh.nu/example. Created randomly if not specified) |
| campaigns | List<String> | X | List of campaign IDs to belong to |
| startDateTime | String | X | Date and time to start using shortURL |
| endDateTime | String | X | Date and time to end the use of shortUrl |

* When adding **startDateTime** and **endDateTime**, use the **DateTimeFormatter.ISO_OFFSET_DATE_TIME** format.
* If **startDateTime** is not specified, it is set to the current time. If **endDateTime** is not specified, it is set to 3 months after **startDateTime**.

```json
{
  "url": "https://nhn.com",
  "domain": "nh.nu",
  "campaigns": [1,2],
  "backHalf": "example",
  "startDateTime" : "2022-11-10T02:58Z",
  "endDateTime": "2100-02-10T02:58Z"
}
```

#### Response
```json
{
  "header": {
    "isSuccessful": true,
    "resultCode": 0,
    "resultMessage": "SUCCESS"
  },
  "body": {
    "shortUrl": "http://nh.nu/example",
    "originUrl": "https://nhn.com",
    "status": "CUSTOM",
    "backHalfType": "AUTO",
    "startDateTime" : "2022-11-10T02:58Z",
    "endDateTime": "2100-02-10T02:58Z"
  }
}
```

| Name | Type | Description |
|---|---|---|
| header.isSuccessful | Boolean | Successful or not |
| header.resultCode | Integer | Result code |
| header.resultMessage | String | Failure message |
| body.shortUrl | String | Shortened URL |
| body.originUrl | String | Full URL |
| body.status | String | Shortened URL status |
| body.backHalfType | String | Method of creating the shortened URL |
| body.startDateTime | String | Date and time to start using the shortened URL |
| body.endDateTime | String | Date and time to end the use of the shortened URL |

* When accessing the original URL through the shortened URL created, the original URL is converted into an ASCII (7) string and added to the Location header.
* In this case, the character + is used without any additional encoding.
    * For example, `https://nhn.com?query=안+녕` is converted to `https://nhn.com?query=%EC%95%88+%EB%85%95` and the character `+ ` is not encoded separately as `%2B`.

### 2. Search
- Search for a shortened URL.

[URL]

```http
GET /open-api/v1.0/appkeys/{appKey}/domains/{domain}/urls/{backHalf}
```

#### Request

[Path Variables]

| Name | Type | Required | Description |
|---|---|---|---|
| appKey | String | O | Service Appkey (Can be found on the **Manage Service** tab) |
| domain | String | O | Domain name |
| backHalf | String | O | Shortened URL path ID |


#### Response
```json
{
  "header": {
    "isSuccessful": true,
    "resultCode": 0,
    "resultMessage": "SUCCESS"
  },
  "body": {
    "shortUrl": "http://nh.nu/a",
    "originUrl": "https://nhn.com",
    "status": "ACTIVE",
    "backHalfType": "AUTO",
    "startDateTime": "2021-03-26T03:35+0000",
    "endDateTime": "9999-12-31T00:00+0000"
  }
}
```

| Name | Type | Description |
|---|---|---|
| header.isSuccessful | Boolean | Successful or not |
| header.resultCode | Integer | Result code |
| header.resultMessage | String | Failure message |
| body.shortUrl | String | Shortened URL |
| body.originUrl | String | Full URL |
| body.status | String | Shortened URL status |
| body.backHalfType | String | Method of creating the shortened URL |
| body.startDateTime | String | Date and time to start using the shortened URL |
| body.endDateTime | String | Date and time to end the use of the shortened URL |



### 3. Search for a QR code
- Search for the QR code of a shortened URL.

[URL]

```http
GET /open-api/v1.0/appkeys/{appKey}/domains/{domain}/urls/{backHalf}/qrcode
```

#### Request

[Path Variables]

| Name | Type | Required | Description |
|---|---|---|---|
| appKey | String | O | Service Appkey (Can be found on the **Manage Service** tab) |
| domain | String | O | Domain name |
| backHalf | String | O | Shortened URL path ID |

#### Response
```json
{
  "header": {
    "isSuccessful": true,
    "resultCode": 0,
    "resultMessage": "SUCCESS"
  },
  "body": "iVBORw0KGgoAAAANSUhEUgAAAIIAAACCAQAAAACieC1QAAAA+0lEQVR4Xu3UsZHEIAwFUO0QkO024BnaIKMlbwNnuwHTkjO3wYwasDMCBp18wbHrxFJ6t4rMCzTigwE61QIf+ZOSAGizNILRCFIuj0yRPzQyeqoeZ9AKVjB6ScN66nMtlGmD0y4uhfPB2eN7Ypdy1JSPpUbSsHTPTNXqBEL6CtCDU8kdMC4urm0XAqGJuA+N9jcfiZS7L73FqaUqkfRcu4HMTk4jPHDpvdvbzCKpgcd2fIgq2Xx342w9aeSnlcWqk+OOcThzS1UifJ95aWpoO5UI/6ezB3h5E2TCb0J5vKQqExoD7rnNLBHK6ZaRUSNHPnExcVXJW33kX8g3k5xLHpTtgoMAAAAASUVORK5CYII="
}
```

| Name | Type | Description |
|---|---|---|
| header.isSuccessful | Boolean | Successful or not |
| header.resultCode | Integer | Failure Code (0: Normal) |
| header.resultMessage | String | Failure message |
| body | String | Base64-encoded PNG image |
