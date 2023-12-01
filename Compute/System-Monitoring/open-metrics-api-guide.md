## Compute > System Monitoring > API Guide

### Basic information
http API Endpoint

| Region | Endpoint |
| --- | --- |
| Korea (Pangyo) Region | https://kr1-api-sysmon.cloud.toast.com |
| Korea (Pyeongchon) Region | https://kr2-api-sysmon.cloud.toast.com |
| United States Region | https://us1-api-sysmon.cloud.toast.com |
| Japan Region |    https://jp1-api-sysmon.cloud.toast.com |

## Prometheus API

### 1. Prometheus Metrics Query API
- You can use Prometheus metrics query API.

[URL]

```http
[GET,POST] /prometheus/{prometheus-api-endpoint}
Content-Type: application/json
```

#### Request

[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |

```
curl "https://kr1-api-sysmon.cloud.toast.com/prometheus/api/v1/series?match[]=query&start=1621894796&end=1621905566" -v -H'X-TC-APP-KEY:appkey'
```

#### Result

```
{
    "status": "success",
    "data": [
        {
            "__name__": "name",
            "domainname": "(none)",
            "instance": "instance",
            "job": "job",
            "machine": "x86_64",
            "nodename": "nodename",
            "openmetrics_id": "uuid",
            "release": "3.10.0-1127.19.1.el7.x86_64",
            "sysname": "Linux",
            "version": "#1 SMP Tue Aug 25 17:23:54 UTC 2020"
        },
        {
            "__name__": "name",
            "domainname": "(none)",
            "instance": "instance",
            "job": "job",
            "machine": "x86_64",
            "nodename": "nodename",
            "openmetrics_id": "uuid",
            "release": "3.10.0-1127.18.2.el7.x86_64",
            "sysname": "Linux",
            "version": "#1 SMP Sun Jul 26 15:27:06 UTC 2020"
        }
    ]
}
```

For more information, refer to [Prometheus HTTP API](https://prometheus.io/docs/prometheus/latest/querying/api/)

#### Available Endpoints

| Method | endpoint |
| --- | --- |
| GET | /prometheus/api/v1/query |
| POST | /prometheus/api/v1/query |
| GET | /prometheus/api/v1/query_range |
| POST | /prometheus/api/v1/query_range |
| GET | /prometheus/api/v1/series |
| POST | /prometheus/api/v1/series |
| GET | /prometheus/api/v1/labels |
| POST | /prometheus/api/v1/labels |
| GET | /prometheus/api/v1/label/\{label_name\}/values |
| GET | /prometheus/api/v1/metadata |

### 2. Grafana Integration
- You can use the Prometheus metrics query API by integrating it with Grafana.

#### 2.1 What is Grafana?

- Grafana is a tool that provides a dashboard that visualizes metrics data.

#### 2.2 How to Use Grafana

- After installing Grafana, log in to Grafana.
- Go to Configuration -> Data sources.
- Click Add data source on the right.
- Choose Prometheus.
![Grafana](https://static.toastoven.net/prod_system_monitoring/console_guide/grafana_guidefile.png)
- In the window where Prometheus is selected, enter Name, URL, and Header in order.
- For URL, you must enter the address of the API Gateway (for example, kr1-api-sysmon.cloud.toast.com) followed by the prefix to use the Prometheus API (/prometheus). (For example, https://kr1-api-sysmon.cloud.toast.com/prometheus)
- For Header, enter x-tc-app-key as the key. For Value, enter the appkey of the System Monitoring product. (You can check the appkey from the URL & Appkey in the upper right corner of Compute > System Monitoring.)
- Click the Save & test button at the bottom and check if "Data source is working" is displayed normally.
- When you return to the main screen, you can see that the newly created data source has been added to the list.



## OpenMetrics Dashboard Workspace API
- You can use the API to query, create, modify, and delete workspaces in the OpenMetrics dashboard.

#### Common Error Codes
| Response Code | Description|
| --- | --- |
| 401 | Appkey was not entered or the entered Appkey is invalid.  |
| 403 | An attempt was made to access an inaccessible project.      |

### 1. Query all OpenMetrics dashboard workspaces

[URL]
```http
[GET] /v1.0/projects/{projectId}/jobs
```

#### Request
[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |
| X-SYSMON-REGION | regionCode    | O | Enter the code of the region you want to query. (kr, kr2, jp, us) |

```
curl -i -X GET \
   -H "X-TC-APP-KEY:appkey" \
   -H "X-SYSMON-REGION:kr" \
 'https://kr1-api-sysmon.cloud.toast.com/v1.0/projects/{projectId}/jobs'
```

#### Response

| Key | Description|
| --- | --- |
| header.isSuccessful   | Whether the API call was successful | 
| header.resultCode     | API call result code |
| header.resultMessage  | API call result message|  
| body[].jobId          | Workspace ID      | 
| body[].projectId      | Project ID      |
| body[].jobName        | Workspace name     |  
| body[].metricsPath    | Workspace URL path | 
| body[].description    | Workspace description     |
| body[].lstModifier    | Last modifier's UUID   |  
| body[].lstModYmdt     | Last modified date      |  
| body[].reservedJobCd  | Workspace creation type (if null, the user creates the workspace manually)  |  

[Example]
```
{
    "header":{
      "isSuccessful": true,
      "resultCode": 0,
      "resultMessage": "SUCCESS"
   },
   "body":[
      {
         "jobId": "jobId",
         "projectId": "projectId",
         "jobName": "jobName",
         "metricsPath": "/metricPath",
         "description": "description",
         "lstModifier": "lstModifier",
         "lstModYmdt": "2021-08-17T10:32:09",
         "reservedJobCd": null
      }
   ]
}
```

### 2. Create an OpenMetrics dashboard workspace

[URL]
```http
[POST] /v1.0/projects/{projectId}/jobs
```

#### Request
[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |
| X-SYSMON-REGION | regionCode    | O | Enter the code of the region where you want to create a workspace. (kr, kr2, jp, us) |
| Content-Type    | content Type  | O | application/json |

[Request Body]

| Key | Value | Required | Note|
| --- | --- | --- | --- |
| jobName       | Workspace name     | O |  |
| metricsPath   | Workspace URL path | O |  |
| description   | Workspace description     |   |  |  

[Error Codes]

| Response Code | resultCode | resultMessage         | Description |
| ---           | ---        | ---                   | --- |
| 200           |  -40001    | ALREADY_EXIST         | The entered value already exists. |
| 200           |  -40002    | BAD_INPUT_VALUE       | Invalid API input. |
| 200           |  -50000    | INTERNAL_SERVER_ERROR | A server error has occurred.  |

```
curl -i -X POST \
   -H "X-TC-APP-KEY:appkey" \
   -H "X-SYSMON-REGION:kr" \
   -H "Content-Type:application/json" \
   -d \
   '{"jobName": "jobName",
   "metricsPath": "/metricPath",
   "description": "description"
   } ' \
 'https://kr1-api-sysmon.cloud.toast.com/v1.0/projects/{projectId}/jobs'
```

#### Response

| Key | Description|
| --- | --- |
| header.isSuccessful  | Whether the API call was successful | 
| header.resultCode    | API call result code |
| header.resultMessage | API call result message|  
| body.jobId           | Created workspace ID      | 
| body.projectId       | Project ID      |
| body.jobName         | Created workspace name     |  
| body.metricsPath     | Created Workspace URL Path | 
| body.description     | Created workspace description     |
| body.lstModifier     | Last modifier's UUID   |  
| body.lstModYmdt      | Last modified date      |  
| body.reservedJobCd   | Workspace creation type (if null, the user creates the workspace manually)  |  

[Example]
```
{
    "header":{
      "isSuccessful": true,
      "resultCode": 0,
      "resultMessage": "SUCCESS"
   },
   "body":{
      "jobId": "jobId",
      "projectId": "projectId",
      "jobName": "jobName",
      "metricsPath": "/metricsPath",
      "description": "description",
      "lstModifier": null,
      "lstModYmdt": "2021-08-17T10:30:06",
      "reservedJobCd": null
   }
}
```

### 3. Query an individual OpenMetrics dashboard workspace

[URL]
```http
[GET] /v1.0/projects/{projectId}/jobs/{jobId}
```

#### Request
[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |

```
curl -i -X GET \
   -H "X-TC-APP-KEY:appkey" \
 'https://kr1-api-sysmon.cloud.toast.com/v1.0/projects/{projectId}/jobs/{jobId}'
```

#### Response

| Key | Description|
| --- | --- |
| header.isSuccessful  | Whether the API call was successful | 
| header.resultCode    | API call result code |
| header.resultMessage | API call result message|  
| body.jobId           | Workspace ID      | 
| body.projectId       | Project ID      |
| body.jobName         | Workspace name     |  
| body.metricsPath     | Workspace URL path | 
| body.description     | Workspace description     |
| body.lstModifier     | Last modifier's UUID   |  
| body.lstModYmdt      | Last modified date      |  
| body.reservedJobCd   | Workspace creation type (if null, the user creates the workspace manually)  |  

[Example]
```
{
    "header":{
      "isSuccessful": true,
      "resultCode": 0,
      "resultMessage": "SUCCESS"
   },
   "body":{
      "jobId": "jobId",
      "projectId": "projectId",
      "jobName": "jobName",
      "metricsPath": "/metricPath",
      "description": "description",
      "lstModifier": "lstModifier",
      "lstModYmdt": "2021-08-17T10:32:09",
      "reservedJobCd": null
   }
}
```

### 4. Modify the OpenMetrics dashboard workspace

[URL]
```http
[PUT] /v1.0/projects/{projectId}/jobs/{jobId}
```

#### Request
[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |
| Content-Type    | content Type  | O | application/json |

[Request Body]

| Key | Value | Required | Note|
| --- | --- | --- | --- |
| metricsPath   | Workspace URL path | O |  |
| description   | Workspace description     |   |  |

[Error Codes]

| Response Code | resultCode | resultMessage         | Description |
| ---           | ---        | ---                   | --- |
| 200           |  -40002    | BAD_INPUT_VALUE       | Invalid API input. |
| 200           |  -40006    | NOT_FOUND_JOB         | No jobId entered.   |
| 200           |  -40012    | SYSTEM_RESERVED_JOB   | The default workspace cannot be modified. |
| 200           |  -50000    | INTERNAL_SERVER_ERROR | A server error has occurred.  |

```
curl -i -X PUT \
   -H "X-TC-APP-KEY:appkey" \
   -H "Content-Type:application/json" \
   -d \
   '{
   "metricsPath": "/updatemetricsPath",
   "description": "updatedescription"
   } ' \
 'https://kr1-api-sysmon.cloud.toast.com/v1.0/projects/aOpreudC/jobs/{jobId}'
```

#### Response

| Key | Description|
| --- | --- |
| header.isSuccessful  | Whether the API call was successful | 
| header.resultCode    | API call result code |
| header.resultMessage | API call result message|  
| body.jobId           | Workspace ID      | 
| body.projectId       | Project ID      |
| body.jobName         | Workspace name     |  
| body.metricsPath     | Modified workspace URL Path | 
| body.description     | Modified workspace description     |
| body.lstModifier     | Last modifier's UUID   |  
| body.lstModYmdt      | Last modified date      |  
| body.reservedJobCd   | Workspace creation type (if null, the user creates the workspace manually)  |  

[Example]
```
{
   "header":{
      "isSuccessful": true,
      "resultCode": 0,
      "resultMessage": "SUCCESS"
   },
   "body":{
      "jobId": "jobId",
      "projectId": "projectId",
      "jobName": "jobName",
      "metricsPath": "/updatemetricsPath",
      "description": "updatedescription",
      "lstModifier": null,
      "lstModYmdt": "2021-08-17T10:35:06",
      "reservedJobCd": null
   }
}
```

### 5. Delete the OpenMetrics Dashboard workspace

[URL]
```http
[DELETE] /v1.0/projects/{projectId}/jobs/{jobId}
```

#### Request
[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |

[Error Codes]

| Response Code | resultCode | resultMessage         | Description |
| ---           | ---        | ---                   | --- |
| 200           |  -40006    | NOT_FOUND_JOB         | No jobId entered.   |
| 200           |  -40012    | SYSTEM_RESERVED_JOB   | The default workspace cannot be deleted. |
| 200           |  -50000    | INTERNAL_SERVER_ERROR | A server error has occurred.   |

```
curl -i -X DELETE \
   -H "X-TC-APP-KEY:appkey" \
 'https://kr1-api-sysmon.cloud.toast.com/v1.0/projects/aOpreudC/jobs/{jobId}'
```

#### Response

| Key | Description|
| --- | --- |
| header.isSuccessful  | Whether the API call was successful | 
| header.resultCode    | API call result code |
| header.resultMessage | API call result message|  
| body                 | Deleted workspace ID | 

[Example]
```
{
   "header":{
      "isSuccessful": true,
      "resultCode": 0,
      "resultMessage": "SUCCESS"
   },
   "body": "jobId"
}
```

## OpenMetrics Dashboard Collection Target API
- You can use the API to query, create, and delete collection targets of the OpenMetrics dashboard.

#### Error codes
| Response Code | Message | Description|
| --- | --- | --- |
| 401 |     | Appkey was not entered or the entered Appkey is invalid. |
| 403 |     | An attempt was made to access an inaccessible Project.       |

### 1. Query all OpenMetrics dashboard collection targets

[URL]
```http
[GET] /v1.0/projects/{projectId}/jobs/{jobId}/targets
```

#### Request
[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |

```
 curl -i -X GET \
   -H "X-TC-APP-KEY:appkey" \
 'https://kr1-api-sysmon.cloud.toast.com/v1.0/projects/{projectId}/jobs/{jobId}/targets

```

#### Response

| Key | Description|
| --- | --- |
| header.isSuccessful   | Whether the API call was successful | 
| header.resultCode     | API call result code |
| header.resultMessage  | API call result message|  
| body[].targetId       | Collection target ID      | 
| body[].jobId          | Workspace ID      | 
| body[].hostId         | Collection target host ID | 
| body[].port           | Collection target port number   | 
| body[].resultCd       | Collection target connection result code| 
| body[].failReason     | Reason for failure to connect to a collection target| 
| body[].mntrnStatCd    | Collection target monitoring status code| 
| body[].lstModifier    | Last modifier's UUID   |  
| body[].lstModYmdt     | Last modified date      |  
| body[].hostNm         | Collection target name     |  
| body[].svrIp          | Collection target IP      |  

[Example]
```
{
    "header":{
      "isSuccessful": true,
      "resultCode": 0,
      "resultMessage": "SUCCESS"
   },
   "body":[
      {
         "targetId": "targetId",
         "jobId": "jobId",
         "hostId": "hostId",
         "port": 9100,
         "resultCd": 0,
         "failReason": null,
         "mntrnStatCd": null,
         "lstModifier": "lstModifier",
         "lstModYmdt": "2021-08-17T11:06:29",
         "hostNm": "hostNm",
         "svrIp": "192.168.0.5"
      }
   ]
}
```

### 2. Query an OpenMetrics dashboard collection target server

[URL]
```http
[GET] /v1.0/projects/{projectId}/servers
```

#### Request
[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |
| X-SYSMON-REGION | regionCode    | O | Enter the code of the region you want to query. (kr, kr2, jp, us) |

```
 curl -i -X GET \
   -H "X-TC-APP-KEY:appkey" \
   -H "X-SYSMON-REGION:kr" \
 'https://kr1-api-sysmon.cloud.toast.com/v1.0/projects/{projectId}/servers'

```

#### Response

| Key | Description|
| --- | --- |
| header.isSuccessful   | Whether the API call was successful | 
| header.resultCode     | API call result code |
| header.resultMessage  | API call result message|  
| body[].hostId        | Host ID        | 
| body[].hostNm        | Hostname       | 
| body[].projectId     | Project ID      | 
| body[].svrIp         | Server IP        | 
| body[].instanceId    | Instance ID       | 

[Example]
```
{
   "header":{
      "isSuccessful": true,
      "resultCode": 0,
      "resultMessage": "SUCCESS"
   },
   "body":[
      {
      "hostId": "hostId",
      "hostNm": "hostNm",
      "svrIp": "192.168.0.5",
      "projectId": "projectId",
      "instanceId": "instanceId"
      }
   ]
}
```

### 3. Create an OpenMetrics dashboard collection target

[URL]
```http
[POST] /v1.0/projects/{projectId}/jobs/{jobId}/targets
```

#### Request
[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |
| Content-Type    | content Type  | O | application/json |

[Request Body]

| Key | Value | Required | Note|
| --- | --- | --- | --- |
| hostId        | Host ID to add as a collection target| O | Host ID retrieved by /v1.0/projects/{projectId}/servers. |
| port          | Collection target PORT    | O |  |

[Error Codes]

| Response Code | resultCode | resultMessage         | Description |
| ---           | ---        | ---                   | --- |
| 200           |  -40002    | BAD_INPUT_VALUE       | Invalid API input. |
| 200           |  -40004    | INVALID_HOST_OR_PROJECT | The entered hostId or projectId is invalid. |
| 200           |  -40006    | NOT_FOUND_JOB         | No jobId entered.   |
| 200           |  -40012    | SYSTEM_RESERVED_JOB   | It cannot be added to the default workspace. |
| 200           |  -50000    | INTERNAL_SERVER_ERROR | A server error has occurred.   |

```
curl -i -X POST \
   -H "X-TC-APP-KEY:appkey" \
   -H "Content-Type:application/json" \
   -d \
   '{"hostId": "host id",
   "port": "post number"
   } ' \
 'https://kr1-api-sysmon.cloud.toast.com/v1.0/projects/{projectId}/jobs/{jobId}'

```

#### Response

| Key | Description|
| --- | --- |
| header.isSuccessful | Whether the API call was successful | 
| header.resultCode   | API call result code |
| header.resultMessage| API call result message|  
| body                | Generated collection target ID | 

[Example]
```
{
   "header":{
      "isSuccessful": true,
      "resultCode": 0,
      "resultMessage": "SUCCESS"
   },
   "body": "targetId"
}
```

### 4. Query an individual OpenMetrics dashboard collection target

[URL]
```http
[GET] /v1.0/projects/{projectId}/jobs/{jobId}/targets/{targetId}
```

#### Request
[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |

```
 curl -i -X GET \
   -H "X-TC-APP-KEY:appkey" \
 'https://kr1-api-sysmon.cloud.toast.com/v1.0/projects/{projectId}/jobs/{jobId}/targets/{targetId}

```

#### Response

| Key | Description|
| --- | --- |
| header.isSuccessful | Whether the API call was successful | 
| header.resultCode   | API call result code |
| header.resultMessage| API call result message|  
| body.targetId       | Collection target ID      | 
| body.jobId          | Workspace ID      | 
| body.hostId         | Collection target host ID | 
| body.port           | Collection target port number   | 
| body.resultCd       | Collection target connection result code| 
| body.failReason     | Reason for failure to connect to a collection target|
| body.mntrnStatCd    | Monitoring status code    | 
| body.lstModifier    | Last modifier's UUID   |  
| body.lstModYmdt     | Last modified date      |  
| body.hostNm         | Collection target name     |  
| body.svrIp          | Collection target IP      |  

[Example]
```
{
    "header":{
      "isSuccessful": true,
      "resultCode": 0,
      "resultMessage": "SUCCESS"
   },
   "body":{
      "targetId": "targetId",
      "jobId": "jobId",
      "hostId": "hostId",
      "port": 9100,
      "resultCd": 0,
      "failReason": null,
      "mntrnStatCd": null,
      "lstModifier": "lstModifier",
      "lstModYmdt": "2021-08-17T11:06:29",
      "hostNm": "hostNm",
      "svrIp": "192.168.0.5"
   }
}
```

### 5. Delete an OpenMetrics dashboard collection target

[URL]
```http
[DELETE] /v1.0/projects/{projectId}/jobs/{jobId}/targets/{targetId}
```

#### Request
[Request Header]

| Header name | Value | Required | Note|
| --- | --- | --- | --- |
| X-TC-APP-KEY    | projectAppkey | O | You can check it from the URL & Appkey in the upper right corner of Compute > System Monitoring. |

[Error Codes]

| Response Code | resultCode | resultMessage         | Description |
| ---           | ---        | ---                   | --- |
| 200           |  -40006    | NOT_FOUND_JOB         | No jobId entered.     |
| 200           |  -40007    | NOT_FOUND_TARGET      | No targetId entered.  |
| 200           |  -40012    | SYSTEM_RESERVED_JOB   | It cannot be deleted from the default workspace. |
| 200           |  -50000    | INTERNAL_SERVER_ERROR | A server error has occurred.    |

```
curl -i -X DELETE \
   -H "X-TC-APP-KEY:appkey" \
 'https://kr1-api-sysmon.cloud.toast.com/v1.0/projects/{projectId}/jobs/{jobId}/targets/{targetId}'

```

#### Response

| Key | Description|
| --- | --- |
| header.isSuccessful | Whether the API call was successful | 
| header.resultCode   | API call result code |
| header.resultMessage| API call result message|  
| body                | Deleted collection target ID | 

[Example]
```
{
   "header":{
      "isSuccessful": true,
      "resultCode": 0,
      "resultMessage": "SUCCESS"
   },
   "body": "targetId"
}
```
