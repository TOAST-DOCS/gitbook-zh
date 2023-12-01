## Contact Center > Online Contact > API Guide for Developers > Member Integration (POST)

## Member Integration
### Overview
Member Intergration function is designed to apply membership confirmation process of the client to the Online Contact help center. Through this function, members of the client service could submit member inquiries, and check the history of previous inquiries. Member Integration is provided in two types: GET method and POST method. For integrating, API needs to be developed according to the development specifications Online Contact provide.

#### POST Method

- It is suitable if the service you are trying to integrate is provided based on WEB on both PC and MOBILE platforms.
- The login page of the service must be provided in WEB URL format.
- Client-side API, Servicer-side API are provided.

#### GET Method

- Suitable for services without WEB-based login page.
- Suitable for Native APP services which are not WEB-based.

### Process (POST Method)

① User accesses to 'Inquiry' or 'Inquiry History' page in the help center.
② In help center page, call 'Login status URL' to check login status('Login status URL' should be developed according to the specifications provided below, and registered in Member Integration menu.)
③ After checking the login status, depending on the result,
③-1. If the user is logged out, call 'Login URL' of the client service to encourage log in('Login URL' is the login page URL provided by the client service. It must be registered in the Member Integration menu.)
③-2. If the user is logged in, call 'Remote Login API' to deliver information of the customer to Online Contact help center.
④ Gain access to 'Inquiry' or 'Inquiry History' page.

### How to Integrate

![](http://static.toastoven.net/prod_contact_center/dev_post_(1)_2_en.png)
① Access Service Management > Help Center > Member Integration
② Enable 'Member Integration'
③ Select whether to enable 'Non-member Inquiry'(If enabled, inquiries can be received even when the user is logged out, and if disabled, inquiries can be received only when the user is logged in)
④ Select the 'Login Type' which matches the characteristics of the service
⑤ Develop and register necessary API

## Development Specifications
### Create Authentication Token
The following is the authentication token generation sample. The order of parameters must be consistent with the given example.
OC Organization Key is available at Global Management → Contract Service Status → Organization Information menu.
(※ Save organization key in Sample project > application.properties > oc.apikey property)

```
private String getSHA256Token(String serviceId, String usercode, String username, String email, String phone,
        String returnUrl, Long time, String apiKey) throws Exception {
    StringBuilder sb = new StringBuilder();
    // Order by follow number:
    sb.append(serviceId); // 1
    sb.append("&");
    sb.append(usercode); // 2
    sb.append("&");
    if (StringUtils.isNotBlank(username)) {
        sb.append(username); // 3
        sb.append("&");
    }
    if (StringUtils.isNotBlank(email)) {
        sb.append(email); // 4
        sb.append("&");
    }
    if (StringUtils.isNotBlank(phone)) {
        sb.append(phone); // 5
        sb.append("&");
    }
    　if (StringUtils.isNotBlank(memberno)) {
        sb.append(memberno); // 6
        sb.append("&");
    　}
    if (StringUtils.isNotBlank(returnUrl)) {
        sb.append(returnUrl); // 7
        sb.append("&");
    }
    sb.append(time); // 8

    SecretKeySpec signingKey = new SecretKeySpec(apiKey.getBytes("UTF-8"), "HmacSHA256");
    Mac mac = Mac.getInstance(signingKey.getAlgorithm());
    mac.init(signingKey);
    byte[] rawHmac = mac.doFinal(sb.toString().getBytes("UTF-8"));
    return new String(Base64.encodeBase64(rawHmac));
}

// Sample
// Use this same input, the output is : Ah9M58CQ9RFTShjFuqziQr+0MjmJxN6+bzWxMD71moo=
public static void main(String[] args) throws Exception {
    String s = getSHA256Token("hangame", "testusercode", "testUsername", "test@email.com", "123456789",
    null, 1660095873001L, "7cf2828608274a49a3f06152b2188927");
    System.out.println(s); // Output: Ah9M58CQ9RFTShjFuqziQr+0MjmJxN6+bzWxMD71moo=
}
```

### POST Remote Login API(From client side)
#### Interface Description

- URL: https://{domain}.oc.toast.com/v2/enduser/remote.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/v2/enduser/remote.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description |
|------------|-------|--------|-----|--------|--------------|
|POST Remote Login API(From client side)|HTTPS  |POST    |UTF-8|Redirect    |The user system dynamically generates a form and returns it to the browser, which automatically passes the information of the form to the API. After authentication with the form information delivered from the API, the login cookie value is set when authentication is successful.|

Please refer to the following class in the sample project for **how to call in the user system**.

- FormLoginController.java
- Method: submitLogin  

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|----|------------|----|----|
|Service ID|service|Varchar(50)|O|Service ID|
|User ID    |usercode|Varchar(50)|O|User ID, indicates that the user is unique|
|Username  |username|Varchar(50)|X|Username|
|User Email Address|email|Varchar(100)|X|User email|
|Phone Number         |phone|Varchar(20)|X|Phone number|
|Membership Number          |memberno |Varchar(50)  |X      |Membership number|
|Timestamp of Current Time |time|Long|O|Timeout alert is displayed when the call time exceeds 3 minutes.|
|Authentication Token           |token|Varchar|O|SHA256 calculated by following parameter values and organization key(If non-required parameter values are null or empty, they need not be added to the encryption string. Caution: The order of each value in the string must be consistent with the following example.) SHA256Digest(service & usercode & username & email & phone & memberno & returnUrl & time)|
|Return page URL|returnUrl|Varchar|X|If settings and login are successful, move to the address|

#### Result Data

If returnUrl parameter exists, move to the specified returnUrl.
If returnUrl parameter does not exist, return 'SUCCESS' string.

### POST Remote Login API(From server side)
#### Interface Description

- URL: https://{domain}.oc.toast.com/api/v2/enduser/remote.json
- URL(Dev): https://{domain}.alpha-oc.toast.com/api/v2/enduser/remote.json

|Interface name | Protocol | Call direction | Encoding | Result format | Interface description |
|------------|-------|--------|-----|--------|--------------|
|POST Remote Login API(From server side)|HTTPS  |POST    |UTF-8|String   |User directly calls API from the server. Login cookie value is set after API login has succeeded.|

Please refer to the following class in the sample project for the **how to call in the user system**.

- ApiLoginController.java
- Method: submitLogin

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|-----|----|-----------|-----|----|
|Service ID|service|Varchar(50)|O|Service ID|
|User ID|usercode|Varchar(50)|O|User ID, indicates that the user is unique|
|User Name |username|Varchar(50)|X|User name|
|User Email Address|email|Varchar(100)|X|User email|
|Phone Number|phone|Varchar(20)|X|Phone number|
|Membership number |memberno |Varchar(50) |X    |Membership number|
|Timestamp of Current Time|time|Long|O|Timeout alert is displayed when the call time exceeds 3 minutes.|
|Authentication Token |token|Varchar|O|SHA256 calculated by following parameter values and organization key(If non-required parameter values are null or empty, they need not be added to the encryption string. Caution: The order of each value in the string must be consistent with the following example.) SHA256Digest(service & usercode & username & email & phone & memberno &  time)|

#### Response Data

```
{	
  "header": {	
    "resultCode": 200,	
    "resultMessage": "",	
    "isSuccessful": true	
  },	
  "result": {	
    "content": "xxxxxxaccessTokenxxxxxxx"	
  }	
}	
```

When help center is called, the returned content value is delivered to Online Contact by the Help Center URL as 'accessToken' parameter.
Example: https://nhn-cs.alpha-oc.toast.com/hangame/hc/?accessToken=xxxxxxaccessTokenxxxxxxx

### POST Login URL(User)
#### Interface Description

|Interface name|Protocol|Call direction|Encoding|URL|URL(Dev)|Result format|
|------------|--------|--------|------|--|----------|--------|
|POST Login URL(User)|HTTPS|GET|UTF-8|Provided by user|Provided by user|Redirect|

Login URL of the service side should provide the following functions.

**1) User status: logged out**

- Show login page
- Proceed to login with id/password
- After login has succeeded, create cookie and record login status. Used to check login status.
- After login has succeeded, client or server passes customer information to Online Contact (Refer to POST Remote Login API(From client side), POST Remote Login API(From server side))

**2) User status: logged in**

- After login has succeeded, client or server passes customer information to Online Contact (Refer to POST Remote Login API(From client side), POST Remote Login API(From server side))

#### Request Parameters
|Name |Variable |Data type |Required | Description|
|---------|---------|-----------|---------|----|
|Return URL|returnUrl|Varchar|O|If login has succeeded, move to the URL|

#### POST Login Function Description

**1) User status: logged out**

- ① Move to login page
- ② User logs in
- ③ Service-side server processes user login, creates user-related cookies
- ④ Call POST remote login API(Refer to POST Remote Login API(From client side), POST Remote Login API(From server side))

**2) User status: logged in**

- ① Call POST remote login API(Refer to POST Remote Login API(From client side), POST Remote Login API(From server side))

#### How to Call POST Remote Login API

**1) POST Remote Login(From client side)**

- ① Create login token based on user information, API key
- ② Redirect user information, token to browser
- ③ Create Form. Refer POST Remote Login API(From client side) about parameter details.
- ④ Submit form
- ⑤ Send user information/token through POST Remote Login API
- ⑥ Move to {returnUrl} after login

**2) POST Remote Login(From server side)**

- ① Create login token based on user information, API Key
- ② Call POST Remote Login API(From server side) in server
- ③ Append API call parameters(usercode, time) in the end of returnUrl
  - Example) https://nhn-cs.alpha-oc.toast.com/multilanguage/hc/ticket/list/?usercode=xxxxxx@163.com&time=1566531359635
- ④ Move to {returnUrl}

### POST Login Status API(User)
#### Interface Description

|Interface name|Protocol|Call direction|Encoding|URL|URL(Dev)|Interface Description|Result format|
|------------|--------|--------|------|--|----------|--------|--------------|
|POST Login Status API(User)|HTTPS|GET|UTF-8|Provided by user|Provided by user|User returns JSON data after confirming login based on cookie information. Service-side server requires cross domain connection settings for response.|JSON|

Please refer to the following information on how to set up **cross domain connection**.
```
response.addHeader("Access-Control-Allow-Origin", request.getHeader("origin"));
response.addHeader("Access-Control-Allow-Credentials", "true");
```

Please refer to the following class in the sample project for **implementation method in the user system**.

- FormLoginController.java
- Method: loginStatus

#### Request Parameters

- None

#### Result Data
|Name |Variable |Data type |Required | Description|
|---------|---------|-----------|---------|----|
|javascript function|login        |Boolean|O|Login status. Logged-in: true, Logged-out: false|
|User ID        |usercode|Varchar(50)|X|User ID (Unique). Required if login status is true|

#### Response Body
```
{
"login": "true",
"usercode":"usercodeXXX"
}

{
"login": "false",
"usercode": null
}
```

## Examples of applications
### Sample Code
✔ [Download Sample Code](https://static.toastoven.net/prod_contact_center/oc_sso_sample-20220817.zip)

### Help center example by using iframe
#### 1. Insert Online Contact Help center into user page by iframe
Please refer 'oc_sso_sample/src/main/resources/templates/help_frame.ftl' in the attached Sample Code file.
The name of the iframe must be specified into id = "ocPage".
```
<iframe src="https://${domain}/hangame/hc/?iframe=true" id="ocPage" frameborder="0" scrolling="no" style="padding-top: 60px; box-sizing: unset; height: 100px; width: 100%">
</iframe>
```  

If you set viewport into page, you could use help center in both mobile/web browsers.
```
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=0">
```

#### 2. Check height of Online Contact Help center page, and adjust height of iframe
Please refer to the javascript code in help_frame.ftl.
```
// Listener for OC content height change
window.addEventListener('message',function(event){
    // Set iframe height
    if(event.data > 0) {
    updateHeight(event.data);
    }
});

var updateHeight = function(wrapHeight) {
var iframe = window.document.getElementById('ocPage');
if(iframe != null) {
iframe.style.height = '0px'; 
var setHeight = (document.body.clientHeight > document.body.scrollHeight) ? document.body.clientHeight : document.body.scrollHeight;
var margin = 70;
setHeight = setHeight > wrapHeight ? setHeight : wrapHeight;
iframe.style.height = setHeight + margin + "px";
}
};
```

#### 3. Cookies that need to be set after login process could be acquired on user page
Please refer to the javascript code in help_frame.ftl.
```
// get cookie
function getCookie(name) {
    var arr,reg=new RegExp("(^| )"+name+"=([^;]*)(;|$)");
    if(arr=document.cookie.match(reg))
        return unescape(arr[2]);
    else
        return null;
}
$.when( $.ready ).then(function() {
    var ssotoken = getCookie("sso_test_login");
    var usercode = getCookie("usercode");
    if(ssotoken != null && usercode != null) {
        var signout = $("#signout");
        $("#signout").html("Welcome " + usercode + "! <a href='/logout.nhn'>Sign out</a>");
        $("#signout").show();
        $("#signin").hide();
    }
});
```
