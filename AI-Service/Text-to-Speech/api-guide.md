## AI Service > Text To Speech > API Guide

### Speech Synthesis API

#### Request

- You can check the {appKey} and {secretKey} in the **URL & Appkey** menu at the top of the console.

[URI]

| Method | URI |
|---|---|
| POST | https://speech.api.nhncloudservice.com/v1.0/appkeys/{appKey}/tts |

[Request Header]

| Name | Value | Description |
|---|---|---|
| Authorization | {secretKey} | Security key issued from the console |
| Content-Type | application/json | |

[Request Body]
```
{
    "inputText": "input text",
    "fileType": "WAV",
    "language: "ZH",
    "speaker": "MALE",
    "emotion": "NEUTRAL",
    "pitch": 0,
    "speed": 1,
    "volume": 0
}
```

[Field]

| Name | Type | Required | Default value | Valid range | Description |
|---|---|---|---|---|---|
| inputText | String | Required | | Up to 1,000 characters | Input text |
| fileType | String | Optional | MP3 | MP3/WAV | File format(.mp3, .wav) |
| language | String | Optional | KO | KO/EN/JA/ZH | Language(Korean, English, Japanese, Chinese) |
| speaker | String | Optional | FEMALE | MALE/FEMALE | Voice type(Male, Female) |
| emotion | String | Optional | NEUTRAL | NEUTRAL/DARK/BRIGHT | Voice emotion(Neutral, Dark, Bright) |
| pitch | Float | Optional | 0 | -12~12| Pitch |
| speed | Float | Optional | 1 | 0.5~4 | Speed |
| volume | Float | Optional | 0 | -6~6 | Volume |

#### Response

[Success Response]
* HTTP Status Code: 200
* Content-Type: audio/wav or audio/mpeg
* Body: byte[]

[Failure Response]
* Content-Type: application/json
```
{
    "header": {
        "isSuccessful": false,
        "resultCode": 400,
        "resultMessage": "Bad Request"
    },
    "errorList": [
        {
            "resultCode": 4000001,
            "resultTitle": "Invalid parameter.  (speed)",
            "resultMessage": "Must be equal to or less than  4 "
        },
        {
            "resultCode": 4000001,
            "resultTitle": "Invalid parameter.  (pitch)",
            "resultMessage": "Must be equal to or less than  12 "
        }
    ]
}
```
