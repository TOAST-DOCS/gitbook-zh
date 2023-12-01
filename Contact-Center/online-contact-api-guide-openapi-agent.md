## Contact Center > Online Contact > API Guide for Developers > Agent Management

### View Agent List
#### Interface Descripiton
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/users.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/users.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description |
|------------|-------|--------|-----|--------|--------------|
|View agent list|HTTPS  |GET    |UTF-8|JSON    |View agent list|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|Service ID|serviceId|String|O|{serviceId} set in URL path|
|User Authority|role|String|X|ROLE_FRONT_ADMIN: Administrator, ROLE_FRONT_AGENT: Agent|
|User Name|name|String|X|User name|
|Number of Pages|page|Int|X|Default = 1|
|Items by Page|pageSize|Int|X|Default = 10|

#### Result Data
|Name |Variable |Data type |Required | Description|
|-----|-----|-----------|----|----|
|result.contents|userId|I|O|User ID|
|                |usercode	|String	|O	|User Code|
|                |uuid	|String	|O	|IAM |User ID|
|                |username	|String	|O	|User name|
|                |role	|String	|O	|User authority. ROLE_FRONT_ADMIN : Administrator, ROLE_FRONT_AGENT : Agent|

#### Response Body
```
{
  "header": {
    "resultCode": 200,
    "resultMessage": "",
    "isSuccessful": true
  },
  "result": {
    "contents": [
      {
        "userId": 10058,
        "usercode": "example",
        "username": "Example",
        "uuid": "ef1bd956-6c13-4391-8256-1eb0d840355a",

        "role": "ROLE_FRONT_ADMIN",
      }
    ]
  }
}
```

### Obtain Agent Information
#### Interface Description
- URL:	https://{domain}.oc.toast.com/{serviceId}/openapi/v1/users/{id}.json
- URL (Dev):	https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/users/{id}.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description |
|------------|-------|--------|-----|--------|--------------|
|Detailed query of agents|HTTPS  |GET    |UTF-8|JSON    |Obtain detailed agent information through agent ID|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|Service ID	|serviceId	|String	|O	|{serviceId} set in URL path|
|User ID	|id	        |Int	|O	|{id} set in URL path|

#### Result Data
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|result.contents	|userId	|Int	|O	|User ID|
|	                |usercode	|String	|O	|User Code|
|	                |uuid	|String	|O	|IAM user ID|
|	                |username	|String	|O	|User name|
|	                |role	|String	|O	|User authority. ROLE_FRONT_ADMIN : Administrator, ROLE_FRONT_AGENT : Agent|

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
        "userId": 10058,
        "usercode": "example",
        "username": "Example",
        ""uuid"": ""ef1bd956-6c13-4391-8256-1eb0d840355a"",
        "role": "ROLE_FRONT_ADMIN",
      }
    }
  }
}
```

### Add Agent
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/adduser.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/adduser.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description |
|------------|-------|--------|-----|--------|--------------|
|Add agent|HTTPS  |POST    |UTF-8|JSON    |Add and give authority to agent in selected service|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|Service ID	|serviceId	|String	|O	|{serviceId} set in URL path|
|	         |id	       |String	|O	|IAM user UUID|
|	         |role	     |String	|O	|User authority. ROLE_FRONT_ADMIN : Administrator, ROLE_FRONT_AGENT：Agent|

#### Result Data
|Name |Variable |Data type |Required | Description|
|-----|-----|-----------|------|---|
|result.contents	|userId	|Int	|O	|User ID|
|	                |usercode	|String	|O	|User Code|
|	                |uuid	|String	|O	|IAM user ID|
|	                |username	|String	|O	|User name|
|	                |role	|String	|O	|User authority. ROLE_FRONT_ADMIN : Administrator, ROLE_FRONT_AGENT : Agent|

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
        "userId": 10058,
        "usercode": "example",
        "username": "Example",
        "uuid": "ef1bd956-6c13-4391-8256-1eb0d840355a",
        "role": "ROLE_FRONT_ADMIN",
    }
  }
}
```

### Change Agent Authority
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/users/{id}.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/users/{id}.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description |
|------------|-------|--------|-----|--------|--------------|
|Change agent authority|HTTPS  |PUT    |UTF-8|JSON    |Change agent authority in service|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|Service ID	|serviceId	|String	|O	|{serviceId} set in URL path|
|User ID	|id	|String	|O	|{id} set in URL path|
|User Authority	|role	|String	|O	|ROLE_FRONT_ADMIN : Administrator, ROLE_FRONT_AGENT : Agent|

#### Result Data
|Name |Variable |Data type |Required | Description|
|-----|-----|-----------|-----|----|
|result.content	|userId	|Int	|O	|User ID|
|	                |usercode	|String	|O	|User Code|
|	                |uuid	|String	|O	|IAM user ID|
|	                |username	|String	|O	|User name|
|	                |role	|String	|O	|User authority. ROLE_FRONT_ADMIN : Administrator, ROLE_FRONT_AGENT : Agent|

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
        "userId": 10058,
        "usercode": "example",
        "username": "Example",
        "uuid": "ef1bd956-6c13-4391-8256-1eb0d840355a",
        "role": "ROLE_FRONT_ADMIN",
    }
  }
}
```

### Delete Agent
#### Interface Description
- URL: https://{domain}.oc.toast.com/{serviceId}/openapi/v1/users/{id}.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/{serviceId}/openapi/v1/users/{id}.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description |
|------------|-------|--------|-----|--------|--------------|
|Delete agent|HTTPS/80  |IN(DELETE)    |UTF-8|JSON    |Delete agent in selected service|

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|-----|----------|-----|----|
|Service ID	|serviceId	|String	|O	|{serviceId} set in URL path|
|User ID	|id	|Int	|O	|{id} set in URL path|

#### Result Data
- None