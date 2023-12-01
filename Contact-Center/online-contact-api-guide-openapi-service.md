## Contact Center > Online Contact > API Guide for Developers > Service 

### Service Details
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/api/v2/service.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/api/v2/service.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description | Access restriction|
|------------|-------|--------|-----|--------|--------------|------------|
|Service Details  |HTTPS  |GET    |UTF-8|JSON    |Query service information via service ID|No need|

#### Request Parameters
|Name |Variable |Data type |Variable type|Required | Description|
|-----|---------|----------|-------------|---------|------------|
|Service ID|serviceId|String|path    |O       |Service ID，{serviceId} which is set in URL path|

#### Result Data
|Name |Variable |Data type |Description|
|-----|----|-----------|------|
|result.content	|serviceId	    |String		|Service ID|
|	            |name	        |String		|Service name|
|	            |profile	    |String		|Service background image|
|	            |language	    |String		|Service default language code|
|	            |languages	    |Array		|Service language list|
|	            |languages.code	|String		|Language code|
|	            |languages.name	|String		|Language name|
|	            |languages.orderNo	|Integer		|Language order|
|	            |multiLanguage	|Boolean		|Whether the service is multilingual(true: multilingual, false: monolingual)|

#### Response Body
```
{
    "header": {
        "resultCode": 200,
        "resultMessage": "",
        "isSuccessful": true
    },
    "result": {
        "content": {
            "serviceId": "APISample",
            "name": "APISample",
            "profile": {
                "fileUrl": "https://api-storage.cloud.toast.com/v1/AUTH_226f908c769e48b0bad7d32f9a91717f/service_alpha/WopqM8euoYw89B7i/27316eba2a8a4089b72a9cf18a83e144.png"
            },
            "language": "ko",
            "languages": [
                {
                    "code": "ko",
                    "name": "한국어",
                    "orderNo": 0
                },
                {
                    "code": "ja",
                    "name": "日本語",
                    "orderNo": 1
                },
                {
                    "code": "en",
                    "name": "English",
                    "orderNo": 2
                },
                {
                    "code": "zh",
                    "name": "中文",
                    "orderNo": 3
                },
                {
                    "code": "th",
                    "name": "ไทย",
                    "orderNo": 4
                }
            ],
            "multiLanguage": true
        }
    }
}
```