## Search > Corporation Search > API Guide

By calling APIs as below, closure or cessation of business operations can be queried. 

<br/>

### Request for Query of Business Closure/Cessation
------------------------------------
[HTTP Request]

```
POST   [Content-Type : application/x-www-form-urlencoded]
https://api-corpsearch.nhncloudservice.com/scraping/v1.0/appkeys/{appkey}/requests?p={param}
```

[Path Parameters]

|Name| Data Type | Description |
|---|---|---|
|appkey|	String| AppKey |
|p|	String| Encrypted request body parameter |

[Request Body Parameters]

|Name| Data Type | Description |
|---|---|---|
|custNo|	long| Client number (available on NHN Cloud Console) |
|crtKey|	String| Client authentication key (available on NHN Cloud Console) |
|bnoList|	String| Business registration number (one or many) |

[Example of Request]

```
{"custNo":1
,"crtKey":"qaz!@wsx"
,"bnoList":["1234567890","0123456789","9012345678"]}

Encrypt JSON data in AES256 and process them as URLEncoder(UTF-8) 
rteo7fjjhGlVznybl239YSngEb2Y3VHOSJaM12AGasdyI1Y0pclSFnPo8uD8eHLFJ41AigDRpsXW36aBQoJXkTFhVeTQ4CMJFg8qKUXj%2Bl%2BwxjdkDJxVdCkJlh4Nnvxm
```

[Example of Request URL]

```
https://api-corpsearch.nhncloudservice.com/scraping/v1.0/appkeys/1sdaf3rs34d2/requests?p=rteo7fjjhGlVznybl239YSngEb2Y3VHOSJaM12AGasdyI1Y0pclSFnPo8uD8eHLFJ41AigDRpsXW36aBQoJXkTFhVeTQ4CMJFg8qKUXj%2Bl%2BwxjdkDJxVdCkJlh4Nnvxm
```

[Example of Response]

```
{
    "header": {
        "resultCode": 0,
        "resultMessage": "Properly requested.",
        "successful": true
    },
    "data": {
        "reqNo": 68,
        "reqCnt": 8,
    “reqDate” : “2015-12-10 10:10:10”
}
}
```

[Response]

|Name| Data Type | Description |
|---|---|---|
|reqNo|	long| Request number |
|resultCnt|	int| Requested number of business registration numbers |
|reqDate|	String| Date and time of request |

<br/>

### Check Status of Request for Query of Business Closure/Cessation 
------------------------------------

[HTTP request]

```
GET
https://api-corpsearch.nhncloudservice.com/scraping/v1.0/appkeys/{appkey}/verification?p={param}
```

[Path Parameters]

|Name| Data Type | Description |
|---|---|---|
|appkey|	String| AppKey |
|p|	String| Encrypted request body parameter |

[Request body Parameters]

|Name| Data Type | Description |
|---|---|---|
|custNo|	long| Client number (available on NHN Cloud Console) |
|crtKey|	String| Client authentication key (available on NHN Cloud Console) |
|reqNo|	long| Request number |

[Example of Request]

```
{"custNo":1
,"crtKey":"qaz!@wsx"
,"reqNo":58}

Encrypt JSON data in AES256 and process them as URLEncoder(UTF-8)
TSNRsStai0hQUM5m40dyDxIJsW5TON7QqVYjjhCIjBUKbMFqmiM1xZ8ND5%2Buo5xd
```

[Example of Request URL]

```
https://api-corpsearch.nhncloudservice.com/scraping/v1.0/appkeys/1sdaf3rs34d2/verification?p=TSNRsStai0hQUM5m40dyDxIJsW5TON7QqVYjjhCIjBUKbMFqmiM1xZ8ND5%2Buo5xd
```

[Example of Response]

```
{
    "header": {
        "resultCode": 0,
        "resultMessage": "Properly requested.",
        "successful": true
    },
    "data": {
        "reqNo": 68,
        "resultDate": “2015-11-11 10:10:10”,
}
}
```

[Response]

|Name| Data Type | Description |
|---|---|---|
|reqNo|	long| Request number |
|resultDate|	String| Date and time of completion |

<br/>

### Receive Result of Request for Query of Business Closure/Cessation 
------------------------------------

[HTTP request]

```
GET
https://api-corpsearch.nhncloudservice.com/scraping/v1.0/appkeys/{appkey}/results?p={param}
```

[Path Parameters]

|Name| Data Type | Description |
|---|---|---|
|appkey|	String| AppKey |
|p|	String| Encrypted request body parameter |

[Request body Parameters]

|Name| Data Type | Description |
|---|---|---|
|custNo|	long| Client number (available on NHN Cloud Console) |
|crtKey|	String| Client authentication key (available on NHN Cloud Console) |
|reqNo|	long| Request number |
|scn| String [Y,N] | Query flag of business name [not required] |

[Example of Request]

```
{"custNo":1
,"crtKey":"qaz!@wsx"
,"reqNo":58}

Encrypt JSON data in AES256 and process them as URLEncoder(UTF-8)
TSNRsStai0hQUM5m40dyDxIJsW5TON7QqVYjjhCIjBUKbMFqmiM1xZ8ND5%2Buo5xd
```

[Example of Request URL]

```
https://api-corpsearch.nhncloudservice.com/scraping/v1.0/appkeys/1sdaf3rs34d2/results?p=TSNRsStai0hQUM5m40dyDxIJsW5TON7QqVYjjhCIjBUKbMFqmiM1xZ8ND5%2Buo5xd
```

[Example of Response]

```
{
    "header": {
        "resultCode": 0,
        "resultMessage": "Completely requested for query.",
        "successful": true
    },
    "data": {
        "reqNo": 58,
        "resultCnt": 8,
        "resultDate": "2015-11-11 10:10:10",
        "resultEncrytData": "8LAT2G8kMp1rFby+n0gWIDYhpnO/sDSU2zMyp0tLnb9Y901/+sw5agirJsWgpJm6s81R1uwOyC+zzBOG98H+WrC1zAMHX1U5tcpbgF+RSeQdx//8r6Af1NXQ3FZ/IsVJnhvttKEqnpFVzGt11zhNz1Tunj ㅍ4d+N+MWYEr7BW2izaQXxRlZ0HX8X8lEiJp7JutKO9BKpZbAtR471SsDAtT6gS845CayO2ojA6ujpqtF/v/ZQei+0KEF10eBwutGTmn1i891E7K/NzdsQbu8qeau7Ksx+QrLSm0SaPHrK71XFjincB/xxXp12xc1zsZK3drQQ/U2xbiAY3CPqTXdNjWpj/iBRZaagQcC6VVvlIrMJ4t4O+cr7xsW5iMgmcpg75dPpsa4pkG8V0S9YKGg24TH+qfM7RZ9Xh7m+OSZMQRtbFT4fLLawB4E7mMKRPCBjmR3elQ0vVrNhWZ8kFt+a8C4D+EdWTIplvkS13tKkFFCF4=",
}
}
```

[Response]

|Name| Data Type | Description |
|---|---|---|
|reqNo|	long| Request number |
|resultCnt|	int| Number of completed data |
|resultDate|	String| Date and time of completion |
|resultEncrytData|	String| Encrypted data of business closure/cessation |

Process URLDecoder of corresponding resultEncrytData, and decrypt AES256 

```
[{"bno":"1234567890","bnoCd":"01","bnoCont":"General taxpayer for value-added tax.","bnoDate":"2015-11-11 10:10:10"}
,{"bno":"1234567890","bnoCd":"01","bnoCont":"General taxpayer for value-added tax.","bnoDate":"2015-11-11 10:10:10"}
,{"bno":"1234567890","bnoCd":"01","bnoCont":"General taxpayer for value-added tax.","bnoDate":"2015-11-10 10:10:10"}]
```

|Name| Data Type | Description |
|---|---|---|
|bno|	String| Business registration number |
|bnoCd|	String| Result code |
|bnoCont|	String| Query result |
|bnoDate|	String| Date of query |
|custNm|	String| Business name (included only when scn is Y) |

<br/>

### Check Recent Request Number for Query of Business Closure/Cessation
------------------------------------

[HTTP request]

```
GET
https://api-corpsearch.nhncloudservice.com/scraping/v1.0/appkeys/{appkey}/recent?p={param}
```

[Path Parameters]

|Name| Data Type | Description |
|---|---|---|
|appkey|	String| AppKey |
|p|	String| Encrypted request body parameter |

[Request body Parameters]

|Name| Data Type | Description |
|---|---|---|
|custNo|	long| Client number (available on NHN Cloud Console) |
|crtKey|	String| Client authentication key (available on NHN Cloud Console) |

[Example of Request]

```
{"custNo":1
,"crtKey":"qaz!@wsx"}

Encrypt JSON data in AES256 and process them as URLEncoder(UTF-8)
3Tm2TS3ynvXw3jcgh1SzQcMIBA2EIRp%2FheQSAsWSXHTP0TODL%2FYEL1Iml3Qn1CWn
```

[Example of Request URL]

```
https://api-corpsearch.nhncloudservice.com/scraping/v1.0/appkeys/1sdaf3rs34d2/verification?p=3Tm2TS3ynvXw3jcgh1SzQcMIBA2EIRp%2FheQSAsWSXHTP0TODL%2FYEL1Iml3Qn1CWn
```

[Example of Response]

```
{
    "header": {
        "resultCode": 0,
        "resultMessage": "Properly requested.",
        "successful": true
    },
    "data": {
        "recentReqNo": 68,
        "recentReqDate": “2015-11-11 10:10:10”,
}
}
```

[Response]

|Name| Data Type | Description |
|---|---|---|
|recentReqNo|	long| Recent request number |
|recentReqDate|	String| Recent date/time of request |

<br/>

### Check Requests of Recent 1 Week for Query of Business Closure/Cessation 
------------------------------------

[HTTP Request]

```
GET
https://api-corpsearch.nhncloudservice.com/scraping/v1.0/appkeys/{appkey}/reqlists?p={param}
```

[Path Parameters]

|Name| Data Type | Description |
|---|---|---|
|appkey|	String| AppKey |
|p|	String| Encrypted request body parameter |

[Request body Parameters]

|Name| Data Type | Description |
|---|---|---|
|custNo|	long| Client number (available on NHN Cloud Console) |
|crtKey|	String| Client authentication key (available on NHN Cloud Console) |

[Example of Request]

<pre><code>{"custNo":1
,"crtKey":"qaz!@wsx"}
Encrypt JSON data in AES256 and process them as URLEncoder(UTF-8)
3Tm2TS3ynvXw3jcgh1SzQcMIBA2EIRp%2FheQSAsWSXHTP0TODL%2FYEL1Iml3Qn1CWn</code></pre>


[Example of Request URL]

```
https://api-corpsearch.nhncloudservice.com/scraping/v1.0/appkeys/1sdaf3rs34d2/reqlists?p=3Tm2TS3ynvXw3jcgh1SzQcMIBA2EIRp%2FheQSAsWSXHTP0TODL%2FYEL1Iml3Qn1CWn
```

[Example of Response]

```
{
    "header": {
        "resultCode": 0,
        "resultMessage": "Properly requested.",
        "successful": true
    },
    "data": {
        "reqList ": “[{“reqNo”:68,”reqStatCd”:”REQUEST”,”reqYmdt”:”2015-10-10 10:10:10”,”trtYmdt”:””,”reqCnt”:20}
, [{“reqNo”:69,”reqStatCd”:”COMPLETE”,”reqYmdt”:”2015-10-10 10:10:10”,”trtYmdt”:” 2015-10-12 10:10:10”,”reqCnt”:20}]”
}
}
```

[Response]

|Name| Data Type | Description |
|---|---|---|
|reqNo|	long| Request number |
|reqStatCd|	String| Status of request |
|reqYmdt|	String| Date/time of request |
|trtYmdt|	String| Date/time of receiving result |
|reqCnt|	int| Number of requests |

<br/>

## References 
### Table of Query Result Codes 
|Code| Result |
|---|---|
|00| Business owner who is not operating business |
|01| General taxpayer for value-added tax |
|02| Simplified taxpayer for value-added tax |
|03| Business owner who is exempted from value-added tax |
|04| Non-profit corporations or organization who own original numbers: national institutions |
|05| Ceased business owner |
|06| Closed business owner |
|09| Others |

<br/>

### Encrypt AES 256  

> Use CBC for the development of encryption module, or PKCS5Padding for padding
> [Example] 
Cipher cipher = Cipher.getInstance("AES/CBC/PKCS5Padding")

> Apply UTF-8 to encode character sets 
