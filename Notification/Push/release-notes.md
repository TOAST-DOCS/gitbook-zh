## Notification> Push > Release Notes

### 2022. 02. 15.
#### [Console]
##### 기능 추가
* 토큰 파일 다운로드 기능 추가
    * **토큰** 탭에서 **토큰 파일 다운로드** 기능을 이용해 저장된 토큰들을 파일로 다운로드할 수 있는 기능이 추가되었습니다.
##### 오류 수정
* 발송 내역 저장 시 UID가 'UNKNOWN'으로 저장되는 오류 수정
    * **설정** 탭에서 **발송 내역 저장** 기능 사용 시 만료된 토큰 내역에서 UID가 'UNKOWN'으로 저장되는 오류를 수정했습니다.
* 인증 실패 안내 메일 중복 발송 오류 수정
    * 푸시 메시지 발송 시 인증에 실패하는 경우, 안내 메일이 중복으로 발송되는 오류를 수정했습니다

### March 24, 2020
### [Console]
#### More Features
* Updated Statistics
    * Added the **Statistics Event Key Management** tab. You can add a new statistics event key on console and set it up for message delivery. With messages sent, statistical data are collected as of configured statistics event key, and then you can search from the new statistics tab. 
        * <a href="https://docs.toast.com/zh/Notification/Push/zh/console-guide/#stats-event-key" target="_blank">Direct Link</a>

### [API]
* Added v2.4 API
    * Added a statistics API to query with statistics event key. Statistics APIs of v2.3 are no longer provided. 
        * <a href="https://docs.toast.com/zh/Notification/Push/zh/api-guide/#stats-api" target="_blank">Direct Link</a>
* Added Multi-tenant Tokens 
   * Added the multi-tenant feature allowing a token to be shared by many UIDs. You may attach '#tenant=Tenant_Information' at the end of a token for a token registration. Even if many UIDs share a same token, the token can be maintained if it has different tenant information.  


### Oct. 29, 2019
#### [API]
##### More Features 
* Added Badge Attribute for Android  
    * The badge attribute can be delivered to Android, as well as iOS. 
    With TOAST SDK, the badge delivered onto app icon is automatically displayed. 
* Display Messages excluding HTML for iOS
    * Currently, iOS does not show HTML within push messages, unlike Android. 
    By setting 'True' for 'content.default.style.useHtmlStyle', HTML can be removed from messages before delivered for iOS. 
* Updated Rich Messages to Separate Media for Android and iOS
    * Added 'richMessage.androidMedia' and 'richMessage.iosMedia', other than 'richMessage.media. 
    Rich message has been updated to enable separate media setting for Android and iOS.  
* Changed the 'sourceType' and 'extension' to be Optional for Rich Message Media 
    * 'richMessage.media.sourceType' and 'richMessage.media.extension' have been changed to be optional, not required. 
    No setting is required for media extension, be it external or internal, to deliver rich messages.  
* Action Definition Enabled at Click of Push Messages 
    * Actions (e.g. URL or Scheme) to be executed by the click of a push message can be defined at 'content.default.clickAction'. 
    With TOAST SDK, action is executed automatically.  

### Sept.24, 2019 
#### [API]
##### Bug Fixes 
* Fixed delivery error of iOS rich messages 
    * Fixed error in which image is not properly displayed on iOS if a rich message is delivered while Receive/Confirm Messages is not enabled.  

#### [Console]
##### More Features 
* Querying Token List from Token Tab 
    * Updated to allow query of tokens from token tab without search conditions. 
* Sending Messages to iOS via FCM 
    * Messages can be sent to an iOS app which applies FCM SDK. 
        *  <a href="https://firebase.google.com/docs/cloud-messaging/http-server-ref" target="_blank">Go to FCM Guide</a>
    * By using attributes such as 'notification', 'content_available', or 'mutual_content', messages can be sent to iOS apps via FCM. 

### May 28, 2019 
#### [API]
* Updated Receive/Confirm Message data collection performance
    * We have improved message receiving/confirmation data collection performance.

### March 26, 2019 
#### [API]
##### Bug Fixes
* Fixed an error where the from (to, to) setting does not apply in the invalid token lookup API
    * Invalid token lookup API, there was an error that ignores the settings unless both from and to are set.
    * Fixed to apply period setting even if only one of from and to is set.

#### [Console]
##### More Features
* Added duplicate message prevention function
    * Even if the exact same message is sent several times, it will not be sent for the set time.
    * Unsent messages will fail. The reason for the dispatch failure is "DUPLICATED_MESSAGE_TOKEN".
    * Duplicate criterion is message type, content (content), outgoing contact, reception agreement setting guide, advertisement display position, token.
    * Settings tab "Duplicate message prevention settings" can be set.

### Feb. 26, 2019 
#### [API]
##### More Features
* Added v2.3 API
    * Added Token Delete API. Can be called without Secret Key.
    * Added new push type 'FCM'. You must use 'FCM' instead of 'GCM' when making API calls.

#### [Console]
##### Bug Fixes
Fix broken, typo, link errors
    * Certificates tab Corrected errors and typo in some tooltips.
    * Fixed setting tab typo.
    * Fixed incorrect SDK guide link.

##### More Features
* User console added.

### Dec. 18, 2018
#### [API]
##### Bug Fixes
* Fixed an error that invalid VoIP token was not deleted normally.
    * Fixed an error that prevents APNS_VOIP, APNS_SANDBOXVOIP token from being deleted when sending a message.

### Oct. 30, 2018 
#### [Console]
##### More Features
* Rich message feature added to message sending page
    * You can send a rich message from the Send Message page.
        * <a href="https://docs.toast.com/en/Notification/Push/ko/console-guide/#_3" target="_blank"> Go to Console Guide  </a>
    * Provide preview functionality to see how rich messages are displayed on Android and iOS.
* Added the ability to set the position of the advertisement marker
    * Added the ability to set whether to display the text that indicates that it is an advertising message in the title or content part.
    * You can set it in the setting tab "Ad display position setting".

##### Bug Fixes
* Fixed an error where token lookups are displayed in UTC
    * There was an error displaying the time in UTC when searching for tokens. Corrected to display in your browser's local time.


#### [API]
##### Add Features
* Rich message feature added to message dispatch API
    * Added the ability to display buttons, media (images, movies, sounds) in push messages.
         * <a href="https://docs.toast.com/en/Notification/Push/en/api-guide/#7" target="_blank">Go to API Guide </a>
    * Available in v2.0 message delivery APIs and in apps with the latest SDKs.

#### [SDK]
##### Android
* Added rich message function
    * Rich messages such as buttons, images, large icons, groups can be transmitted.
* Added API for reply function of rich message
    * Listener class registration API has been added to handle reply button.
* Android 9 compatible
    * Fixed bug where receive / open metrics are not collected on Android 9 devices when target version is 28 (Android 9) or higher.

##### iOS
* Added rich message function
    * Rich messages such as buttons, images, and movies can be transmitted.
* Added category setting function
    * If you set the category in the initialization and set it as the category identifier of your own in the message, you can receive the corresponding category action.
* Added indicator collection methodology
    * It is possible to collect verification indices without initialization by inputting the indicator collection information (AppKey) in the application's info.plist file.
    * It is possible to automatically transmit the reception indices by inputting the four index acquisition information (AppKey) of the info.plist file of the user Notification Sarvice Extension. (TCPushServiceExtension extension required)
* Improved token registration
    * Only the system token is registered when the token registration request is made without initialization, and the issued token can be freely registered through the API from the service server.

##### Bug Fixes
* Error that data is missing from 1 second to 59 seconds when querying from list query API to minutes
    * As an example, if you look up data by 10:11, there is an error that the data of 11 minutes 59 seconds is missing.
    In this case, we improved to include 59 seconds.

### Aug. 28, 2018 
#### [API]
##### More Features
* Added Logging API
    * Added API to inquire saved data with Logging function that can be activated in Console.
    * Provides two types of APIs: general query, bulk query.
         * <a href="https://docs.toast.com/en/Notification/Push/en/api-guide/#_18" target="_blank"> Go to Log view </a>
* v2.2 API Update
    * Updated Logging API to update the latest API version to v2.2.
    * As of v2.2, API security setting is used for API authentication.
         * <a href="https://toast.com/account/api_settings" target="_blank"> Go to API Security Settings </a>
    * Supported API versions: v1.3, v2.0, v2.1, v2.2

##### Bug Fixes
* Errors that the APNS_VOIP token is deleted when the app type is set to 'Single Token' in the token setting
    * The APNS_VOIP token is a token for VoIP, so it must be managed separately from the GCM, APNS, etc. for push messages,
    When set to a single token, there was an error that APNS_VOIP was managed the same as other tokens and the APNS_VOIP token was deleted.
    * Modified so that the APNS_VOIP tokens and the GCM, APNS, and TENCENT tokens are managed separately.
* Improved error in statistics API timeout in some projects
    * There was a timeout error in some projects. Fixed timeout not to occur through optimization.

### July 24, 2018 
#### [API]
##### Updates
* Improved response message
    * Improved to better understand the cause of failure in header.resultMessage of Response Body by adding more details.

#### [SDK]
##### Android
* Amazon Device Messaging support

##### iOS
* VoIP type support
* Some API changes due to VoIP type addition

<br>

### June 26, 2018 
#### [Console]
##### More Features
* Add Amazon Device Messaging (ADM) push type
    * Added ADM push type to send push messages to Amazon device (Kindle Fire).
    * You can register your app on the Amazon developer site, get a Client ID, Client Secret, and register it.
     <a href="https://docs.toast.com/en/Notification/Push/en/console-guide/#adm-client-id-client-secret" target="_blank"> ADM Guide Shortcut </ a>


#### [API]
##### More Features
* Add Amazon Device Messaging (ADM) push type

##### Bug fixes
* Fixed an error that caused some targets to be missing when sending a promotional push message
    * Fixed on May 30, 2018 as a hotfix.
    * Fixed an error where some destinations were missing when sending a push message with a shipping logic error.
* Fixed an error that duplicate reception when using local time function when sending reservation message
    * Fixed an error sending a reservation message in a non-existent time zone when using the local time feature.

#### [SDK]
##### Android
* Apply latest Tencent SDK (3.2.3)
* API improvements

##### iOS
* Improvement of indicator collection and transmission function
Automate message check indicator collection and transmission

<br>

### May 29, 2018 
#### [Console]
##### Updates

* Add message ID
    * Added message ID to the details part of popup when selecting message.

#### [API]
##### More Features
* Added v2.1 token lookup API
    * You can check the device ID you collect when you register the token.
    * You can check the date of the most recent registration request for this token.

##### Updates
* Advertising