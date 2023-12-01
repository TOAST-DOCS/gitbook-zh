## Contact Center > Online Contact > API Guide for Developers > Customer Data Connection

This function is provided for obtaining **customer information according to the media number from client company through API** when **call inquiry** has been requested.

Request URL: API URL of client company
Response Type: JSON

### Request Parameters
|Number|Variable|Required|Data Type|Description|
|----|----|----|---------|----|
|1   |telNo|O  |String   |Media number of received call|

### Result Data
|Number|Variable|Data Type|Description|
|----|---|-----------|---|
|1   |resultCode|String|Success:0, Fail:other|
|2   |resultMsg |String|Result message|
|3   |resultData|Map   |Result map|

### resultData parameters
|Number|Variable|Data Type|Description|
|----|----|----------|---|
|1  |custId|String   |   |
|2  |custName|String |   |
|...|...     |...    |...|

### Response Body
```
{
   "resultData":{
      "custId": "test",
      "custName": "Test",
      ..
      ..
   },
   "resultCode": "0",
   "resultMsg": "success"
}
```

The data in the variable resultData could be set as desired by the client company, and **all of the data returned by the API are displayed to the screen.**
If the variable in the resultData is added as ticket field in Online Contact, the **variable name** and **field code** should be **identical** for adequate mapping.
