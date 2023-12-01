## Security > OTP > Developer's Guide

Console에서 OTP 서비스를 활성화 한 후 다음과 같은 API 호출을 통해 OTP 서비스를 이용할 수 있습니다.

|API|	설명|
|---|---|
|otp/v1.0/appkeys/{appkey}/keys|	OTP 인증 키 및 QR 코드 이미지 바이너리 값을 전송함|
|otp/v1.0/appkeys/{appkey}/codes/{code}/verification?userId={userId}&encodedKey={encodedKey}|	OTP 인증 키와 인증 코드의 유효성을 확인함|

## 1. OTP 인증 키 및 QR 코드 획득

아래 API를 호출하여 OTP 인증 키와 QR 코드를 획득합니다.

[URL]

```
POST   https://kr1-otp.api.nhncloudservice.com/otp/v1.0/appkeys/{appKey}/keys
Content-Type  application/json
```

[Path Parameter]

|이름|	자료형|	설명|
|---|---|---|
|appkey|	String|	OTP AppKey|

[Request body Parameter]

|이름|	자료형|	설명|
|---|---|---|
|userId|	String|	사용자 아이디|
|serviceName|	String|	서비스 이름|

[Response body]

|이름|	자료형|	설명|
|---|---|---|
|header|	Header| 결과|
|encodedKey|	String|	OTP Key (서비스에서 저장하여 OTP Code 유효성 체크할 때 파라미터 값으로 사용)|
|qrCodeEncodedString|	String|	QR코드 이미지 바이너리 (Base64.decodeBase64()를 통해 디코딩해서 사용)|

[Header]

|이름|	자료형|	설명|
|---|---|---|
|resultCode|	int|	결과코드 (성공 : 0, 그 외 : 실패)|
|resultMessage|	String|	결과 메시지|
|successful|	boolean|	성공 여부|

[Example Request]

```
URL      https://kr1-otp.api.nhncloudservice.com/otp/v1.0/appkeys/ad89539d41c8363a987034b6c84c962cd8c813c9d6de35ec6b6afbee697aaa7a/keys
application/json  {“userId”: “test”, “serviceName”: “svc”}
```

[Example Response]

```
{
  "header": {
    "resultCode": 0,
    "resultMessage": "SUCCESS"
    "successful": true
  },
  "Key": {
    "encodedKey": "YUI5RSM2QNNRNJ7C",
    "qrCodeEncodedString": "iVBORw0KGgoAAAANSUhEUgAAASwAAAEsAQAAAABRBrPYAAAB80lEQVR42u2aMXLDMAwEoVGh0k/wU/g08ml8ip7g0oVGCHEA5TiKZlKk8pFFEhnrBmMcjueI/uU8ZGADG9jABqZV7NxVp01uWrPM+mhPeFUyI4Y/7zVP+rSKGt3e9KrRYSKLdUq3xZ5lfkYX5c6MVUFBi1r70sCsbqdYvY0UM+aTJbssuh71qwEkwFx7W2FbHq9fFxJNgPVTbAu1wu6r6WqJfz5mfVtaXfbZNKaoK057uq2JETNngi0UdmWfVddUfFdnQsy3kKmtvSLS6s2uoH3y1l4WDCMFmd3gWna3K8SYhpNF+1LZ8aa2muBrGbHuUzT2sTcMvvbbdibC0JumtiHB1kUzL7aakhJikBoTlyjsblT6gBFicPh9pLCWcfPxGyEpJuZMYjv7ZBVz+KtkQsxufdY3l+DUZ01+DiANVvFzFTn8W3Oy3rD3AWTB7Lh33aC9cPgV+dqaGLHaGxa5wHQxgDxYuwYjF0Bs0icL2vvWNyJMwsJ6Kt9TAnysMifmSaPRa/gURAenncWBxYksGlfBMPo3rYxYTxpF4yroSjydtJcGOxaxFeTIXE+TxYPF1zcopAhRrgaQCMsxYJESWGzCjR2dgtRE4KiUWHwnHtu5KU7TmCKnlIAG69ob2xkfJI+kf5Xoj8fGfxANbGADG9j/YF9P1zK9rCNOGQAAAABJRU5ErkJggg=="
  }
}
```

## 2. OTP APP 다운로드 
OTP APP을 다운로드합니다.

- For Android, iOS, and Blackberry: 
	<a href="https://support.google.com/accounts/answer/1066447?hl=en" target="_blank">
		<font class="custom-link">Google Authenticator</font>
	</a>
- For Android and iOS: 
	<a href="http://guide.duosecurity.com/third-party-accounts" target="_blank">
		<font class="custom-link">Duo Mobile</font>
	</a>
- For Windows Phone: 
	<a href="http://www.windowsphone.com/en-us/store/app/authenticator/021dd79f-0598-e011-986b-78e7d1fa76f8" target="_blank">
		<font class="custom-link">Authenticator</font>
	</a>

## 3. OTP APP에 인증 키 정보 입력 
OTP APP을 실행한 후, OTP 인증 키 정보를 입력합니다.

```
* 참고 : OR 코드 스캔하여 OTP APP을 실행하는 방법
	- OTP 인증 키를 획득하면서 얻은 QR코드 값을 Base64 decoding 하여 이미지로 출력합니다.
	- 이미지로 출력된 QR 코드를 스캔합니다.
	- QR 코드를 스캔하면, 인증 키가 자동으로 입력된 채 OTP APP이 실행됩니다.
```
				
## 4. OTP 인증 코드 획득
OTP APP 에서 OTP CODE 값을 획득합니다.

## 5. OTP 인증 코드 확인
아래 API를 호출하여 OTP 인증 코드를 확인합니다.

[URL]

```
GET        https://kr1-otp.api.nhncloudservice.com/otp/v1.0/appkeys/{appKey}/codes/{code}/verification?userId={userId}&encodedKey={encodedKey}
```

[Path Parameter]

|이름|	자료형|	설명|
|---|---|---|
|appkey|	String|	OTP AppKey|
|code|	String|	Mobile OTP 앱을 통해 얻은 OTP 인증 코드|

[Query Parameter]

|이름|	자료형|	설명|
|---|---|---|
|userId|	String|	사용자 아이디|
|encodedKey|	String|	API를 통해 발급 받은 OTP 인증 키|

[Header]

|이름|	자료형|	설명|
|---|---|---|
|resultCode|	int|	결과코드 (성공 : 0, 그 외 : 실패)|
|resultMessage|	String|	결과 메시지|
|successful|	boolean|	성공 여부|

[Example Request]

```
URL otp/v1.0/appkeys/ad89539d41c8363a987034b6c84c962cd8c813c9d6de35ec6b6afbee697aaa7a/codes/269935/verification?userId=test&encodedKey=YUI5RSM2QNNRNJ7C
```

[Example Response]

```
{
  "header": {
    "resultCode": 0,
    "resultMessage": "SUCCESS"
    "successful": true
  }
}
```

## 에러 코드

에러 코드는 다음과 같습니다.

|Code|	설명|
|---|---|
|0|	SUCCESS: 정상|
|-1|	FAIL: 실패|
|-2|	PARAMETER_ERROR : 파라미터 값이 유효하지 않을 때|
|-3|	HTTP_STATUS_ERROR : HTTP status error|
|-4|	APPKEY_ERROR : appkey 값이 유효하지 않을 때|
|-101|	DATA_INVALID_ERROR : 인증 코드가 일치하지 않을 때|
|-102|	DATA_DUPLICATE_ERROR : 기존에 사용된 OTP 인증 키인 경우|
