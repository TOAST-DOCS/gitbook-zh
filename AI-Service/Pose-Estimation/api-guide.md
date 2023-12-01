## AI Service > Pose Estimation > API Guide


### Pose Recognition API

#### Request

- You can check the {appKey} and {secretKey} in the **URL & Appkey** menu at the top of the console.

[URI]

| Method | URI                                                                        |
|---|----------------------------------------------------------------------------|
| POST | https://pose-estimation.api.nhncloudservice.com/v1.0/appkeys/{appKey}/pose |

[Request Header]

| Name | Value | Description              |
|---|---|-----------------|
| Authorization | {secretKey} | Security key issued from the console |

[Path Variable]

| Name | Value | Description              |
| --- | --- |-----------------|
| appKey | {appKey} | Integrated Appkey or Service Appkey |

[Request Body]

- Input the binary data for the image file.

```
curl -X POST 'https://pose-estimation.api.nhncloudservice.com/v1.0/appkeys/{appKey}/pose' \
-F 'image=@sample.png' \
-H 'Authorization: ${secretKey}'
```

[Field]

| Name | Type | Description |
|---|---|---|
| image | multipart/form-data | Image file |

#### Response

[Response Body]

```json
{
  "header": {
    "isSuccessful": true,
    "resultCode": 0,
    "resultMessage": "SUCCESS"
  },
  "result": {
    "fileType": "png",
    "numberOfPerson": 5,
    "keyPointList": [
      {
        "personId": "0",
        "inferKeypointList": [
          {
            "name": "nose",
            "part": "body",
            "x": 367.151489,
            "y": 79.552887,
            "score": 0.976
          },
          {
            "name": "left_eye",
            "part": "body",
            "x": 373.819214,
            "y": 73.5605469,
            "score": 0.985
          },
          ...
        ]
      },
      ...
      {
        "personId": 2,
        "inferKeypoints": [
          {
            "name": "nose",
            "part": "body",
            "x": 98.7361755,
            "y": 68.2939758,
            "score": 0.979
          },
          {
            "name": "left_eye",
            "part": "body",
            "x": 110.171448,
            "y": 56.0753479,
            "score": 0.983
          },
          ...
        ]
      },
    ]
  }
}
```

[Header]

| Name | Type | Description                            |
|---|---|-------------------------------|
| isSuccessful | Boolean | Recognition API success or not                  |
| resultCode | Integer | Result code                         |
| resultMessage | String | Result message (success on success, error content on failure) |

[Field]

| Name                                         | Type      | Description                                      |
|--------------------------------------------|---------|-----------------------------------------|
| fileType                                   | String  | File extension (.jpg, .png)                      |
| numberOfPerson                             | Integer | Number of people recognized                              |
| keyPointList[0].personId                   | String  | ID assigned to distinguish recognition results                     |
| keyPointList[0].inferKeypointList[0].name  | String  | Body part name                                |
| keyPointList[0].inferKeypointList[0].part  | String  | The name of the part the body part belongs to (body, foot, face, hand) |
| keyPointList[0].inferKeypointList[0].x     | Double  | X coordinate of the keypoint                               |
| keyPointList[0].inferKeypointList[0].y     | Double  | Y coordinate of the keypoint                               |
| keyPointList[0].inferKeypointList[0].score | Double  | Confidence in keypoint recognition results                          |



