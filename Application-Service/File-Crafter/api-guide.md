## Application Service > File Crafter > API Guide

### API Overview

#### API Domain

```
https://api-file-crafter.nhncloudservice.com
```

#### AppKey & Secret

- You must add AppKey and Secret Key to headers.
- You can check or create them in **CONSOLE > Application Service > File Crafter > URL & AppKey**.

### Export Request
After sending repetitive requests to the specified URL, the received response is saved as a file and uploaded to the specified storage. The specifications required by the Export callback URL can be found in the [Callback API Guide](./callback-api-guide.md).

#### Request

- [URL]
```
POST /file-crafter/v2.0/export/files 
Content-Type: appliction/json
```

- [Header]
```json
{
  "x-tc-app-key": "String",
  "x-secret-key": "String"
}
```

- [Request body]

```json
{
  "callback": {
    "url": "http://my.service.com/api/export",
    "query": {
      "endOffset": 300,
      "pageSize": 50
    }
  },
  "exportedFile": {
    "extension": "xls",
    "maxRowCountPerFile": 1000,
    "password": "test",
    "fields": {
      "key": "headerName"
    },
    "sheets": [
      {
        "sheetName": "Sheet 1",
        "sheetQuery": "sheetQuery1"
      }
    ]
  },
  "storages": [
    {
      "secretKey": "String",
      "bucketName": "String",
      "endPoint": "https://api-storage.cloud.toast.com",
      "region": "KR1",
      "filePath": "String",
      "fileName": "String",
      "fileFullPath": "String",
      "used": true
    }
  ],
  "searchKey": "localTestType"
}
```

| Value                               | Type      | Constraints          | Required  | Description                                        |
|---------------------------------|----------------|----------------|-------------------------------------------|-------------------------------------------|
| callback                        | Object  | Not Null       | O   | Callback information for export                          | 
| callback.url                    | String  | Not Blank      | O   | URL to call by File Crafter for export        |
| callback.query                  | Object  |                |     | Query sent along when File Crafter calls the specified URL. |
| exportedFile                    | Object  | Not Null       | O   | Information on export result file                           |
| exportedFile.extension          | String  | Not Null       | O   | [xls, xlsx, csv, json]                    |
| exportedFile.maxRowCountPerFile | Integer | 1000 ~ 1000000 |     | Maximum row count per file                               |
| exportedFile.password           | String  |                |     | Password for result file (xls, xlsx formats supported)                |
| exportedFile.fields             | Object  |                |     | Export target field, Item name                       |
| exportedFile.sheets             | Array   |                |     | Query key to distinguish sheets when multiple sheets are exported, Sheet name       |
| storages                        | Array   | Not Empty      |     | Information on storage where result file is uploaded. Up to 5 can be specified.      |
| storages.accessKey              | String  |                |     |                                           |
| storages.secretKey              | String  |                |     |                                           |
| storages.bucketName             | String  |                |     |                                           |
| storages.endPoint               | String  |                |     |                                           |
| storages.region                 | String  |                |     |                                           |
| storages.filePath               | String  |                |     |                                           |
| storages.fileName               | String  |                |     |                                           |
| searchKey                       | String  |                |     | Search key used to retrieve requests in the console                  |

   - exportedFile.fields
      -  Key is extracted from the export callback response and exported as a value.
          
   - ex) exportedFile.fields

```json
 {
     "name": "이름",
     "number": "연락처"
 }
 ```

 - ex) export callback response

```json
 [
   {"name": "Jason", "number": "01012341234"}, 
   {"name":"Tim", "number": "01043214321"}
 ]
```

  - ex) export result

| Name | Contact |
|---|---|
| Jason |01012341234|
| Tim   |01043214321|

- exportedFile.sheets
    - When requesting export callback, sheetQuery parameter is sent, and the response is exported to the sheetName sheet.

- ex) exportedFile.fields

```json
[
    {
      "sheetQuery": "October",
      "sheetName": "10월"
    }
]
```
- ex) export callback request

```
http://my.service.com/api/export?sheetQuery=October
```

### Import Request
Parameterize the uploaded file and make repetitive requests to the specified URL. The specifications required by the import callback URL can be found in the [Callback API Guide](./callback-api-guide.md).

#### Request

- [URL]
```
POST /file-crafter/v2.0/import/files
```

- [Header]
```json
{
  "x-tc-app-key": "String",
  "x-secret-key": "String"
}
```

- [Query parameter]

| Value                     | Type     | Constraints   | Required  | Description                                    |
|-----------------------|---------|---------|---------------------------------------|---------------------------------------|
| importingCallbackUrl | Object |         | O   | URL to call by File Crafter for validation   |
| validatingCallbackUrl  | String |         |     | URL to call by File Crafter for export |
| isAutoImporting       | String |         |    | When validation is included                        |
| dataStartRowNum       | String | At least 2 |     | Row number where actual data starts                     |
| searchKey             | String |         |     | Search key used to retrieve requests in the console               |
| password              | String |         |     | File password when importing an encrypted excel file |

### Common response
Response commonly used by Export and Import requests.

- [Response body]
```json
{
  "header": {
    "resultCode": 0,
    "resultMessage": "success",
    "isSuccessful": true
  },
  "fileId": "String"
}
```
| Value                    | Type      | Description        |
|----------------------|-----------|-------|
| header               | Object  |           |
| header.resultCode    | Integer | Request result code  |
| header.resultMessage | String  | Request result message |
| header.isSuccessful  | Boolean | Request success or not   |
| fileId               | String  | Request ID     |