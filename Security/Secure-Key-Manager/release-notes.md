## Security > Secure Key Manager > Release Notes

### November 28, 2023
#### Added Add/Delete Keys API
* Added the feature to add or delete keys using APIs
* To add or delete keys using APIs, you must need a User Access Key ID and a Secret Access Key. For more information, see [the console user guide](https://docs.nhncloud.com/zh/Security/Secure%20Key%20Manager/zh/console-guide/#authorization-for-adddelete-keys-api)

### September 26, 2023
#### Added IPv4 Bandwidth Authentication Feature
* Added a feature to authenticate bandwith using CIDR notation when authentication with IPv4

### July 25, 2023
### Fixed Approval Process Certificate Cancel Error
* Fixed an error in the approval process where a certificate in the **In Use** status is displayed as **Scheduled to Cancel Deletion** instead of the original **In Use** status when requesting deletion and then canceling the request

### May 30, 2023
#### Fixed Approval Process Notification (email) Error
* Fixed an issue where some managers with approval authority cannot receive notifications (email)
#### Fixed Error in IP/MAC Large Registration of Approval Process
* Fixed an issue where, when registering a large amount of IP/MAC in the approval process, it is not immediately reflected

### April 25, 2023
#### Added Approval Process Notification (email) Feature
* Added a feature to notify the manager with approval authority via email when registering a request for approval

### February 28, 2023
#### Fixed Template File Download Error
* Fixed an issue where bulk registration template file is downloaded as a template in the wrong format

### January 31, 2023
#### Improved Approval Feature and Fixed an Error
* Modified the feature so that, when entering the confidential data editing screen while using the approval feature, the data area is displayed as blank
* Modified the feature so that the edited data is displayed after editing the confidential data

#### Changed Messages
* Fixed an issue where the tooltip messages for MAC address is displayed as IPv4, not MAC address on the key store management tab.

### December 27, 2022
#### Changed API Domain
* Changed the SecureKeyManager API domain from `api-keymanager.cloud.toast.com` to `api-keymanager.nhncloudservice.com`

### November 29, 2022
#### Improved Approval Feature and Fixed an Error
* Modified an error message that occurs while using the approval feature so that it is more understandable
* Fixed an issue where, when initially adding a key store while using the approval feature, it is added without approval procedure
#### Fixed Certificate Authentication Error
* Fixed an issue where certificate authentication fails intermittently

### October 25, 2022
#### Fixed Total Appkey Error
* Fixed an issue where calling APIs with a project total appkey does not work properly.
#### Fixed Approval Feature Error
* Fixed an issue where deletion does not work properly for each key version when using approval feature

### September 27, 2022
#### Added an Asymmetric Key Query Feature
* Added a feature to query the asymmetric key for each key version

### July 26, 2022
#### Added Approval Feature
* Added a feature to approve major changes such as key creation, modification, deletion, and changes to access control for key store
#### Added a new version of Symmetric Key Query Feature
* Added a feature to query the symmetric key for each key version

### November 23, 2021
#### Added a Symmetric Key Query Feature
* Added a feature to query the symmetric key

### October 26, 2021
#### Added a Key Import Feature
* Added a symmetric key import feature
#### Updated the Confidential Data Query Feature
* Modified the feature so that, when the user queries confidential data in the web console, the data is provided after masking the fields
#### Bug Fixes
* Fixed an issue where non-payment users could use the service normally

### September 28, 2021
#### Bug Fixes
* Fixed an issue where permissions granted using permission groups were not recognized properly
* Fixed an issue where the Reset button in Usage History did not work properly

### March 24, 2020
* The tasks performed by a user in Secure Key Manager console are logged in Cloud Trail
* Added authentication data (IPv4 address/MAC address) bulk registration feature using CSV files
* Added authentication data (IPv4 address/MAC address) download feature using CSV files

### December 24, 2019

#### Key Store Page Updates
* Changed the display method for the list of key stores
* Changed the sub-menu of a key store
* Added the quick menu to the key store

#### History Page Updates
* Changed UI so that the user can query API usage history per project

#### Statistics Page
* Added the page to query API usage statistics of each project

### July 23, 2019

#### UI Improvement
* Fixed the overlapped display of texts and buttons
* Fixed line wrapping issue when the screen is displayed in Japanese

### May 28, 2019

#### Release of New Service
* Secure Key Manager is a service to let you centrally and securely manage data that can be exposed to security risks when stored in the application server, such as confidential data (database access information, appkey, password, etc.), symmetric key, and asymmetric key. In addition, it controls access so that only the clients that pass authentication can access the data.
