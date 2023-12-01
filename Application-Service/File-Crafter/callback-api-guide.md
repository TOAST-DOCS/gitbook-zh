## Application Service > File Crafter > Callback API Guide

To use File Crafter’s import and export features, you must provide appropriate callback APIs.
This document describes the requirements of each callback API.

### Export Callback

Callback API for querying paginated lists. You can use two types of parameters for paging.
Export data by calling repeatedly until there are no more query results.

- [HTTP Method]

```
GET
```
- [Content-Type]

```
application/json
```

- [Query parameter]

  | Item                 | Key                 | Description                              |
  |--------------------|-------------------|---------------------------------|
  | Number of data to query at once    | limit or pageSize | Required to use offset or pageNum and set    |             
  | Number of data to skip for paging | offset or pageNum |                                 |
  | Parameter for sheet classification         | sheetQuery        | Parameter to classify sheets when exporting multiple sheets |                              |

- offset, limit parameter set
```json
{
  "offset": 0,
  "limit": 10
}
```

- pageNum, pageSize parameter set

```json
{
  "pageNum": 1,
  "pageSize": 10
}
```

- [Response body]
```json
{
  "data": [
    {
      "key1-1": "value1-1",
      "key2-1": "value2-1"
    },
    {
      "key1-2": "value1-2",
      "key2-2": "value2-2"
    }
  ]
}
```

### Import Callback

Callback API that can receive and process an object array consisting of multiple items.

- [HTTP Method]
```
POST
```
- [Content-Type]
```
application/json
```

- [Request body]
```json
{
  "data": [
    {
      "key1-1": "value1-1",
      "key2-1": "value2-1"
    },
    {
      "key1-2": "value1-2",
      "key2-2": "value2-2"
    }
  ]
}
```
- [Response body]
```json
{
  "header": {
    "resultCode": 0,
    "resultMessage": "success",
    "isSuccessful": true
  },
  "errors": []  
}
```

### Validate Callback

Callback API that can validate if the data is appropriate before requesting import callback. The received request data must be returned as validation success/failure.

- [HTTP Method]

```
POST
```
- [Content-Type]
```
application/json
```

- [Request body]
```json
{
  "data": [
    {
      "key1-1": "value1-1",
      "key2-1": "value2-1"
    },
    {
      "key1-2": "value1-2",
      "key2-2": "value2-2"
    }
  ]
}
```

- [Response body]

```json
{
  "header": {
    "resultCode": 0,
    "resultMessage": "success",
    "isSuccessful": true
  },
  "success": [
    {
      "key1-1": "value1-1",
      "key2-1": "value2-1"
    }
  ],
  "errors": [
    {
      "key1-2": "value1-2",
      "key2-2": "value2-2"
    }
  ]         
}
```