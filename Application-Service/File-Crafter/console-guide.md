## Application Service > File Crafter > Console User Guide

You can request File Crafter service’s features via API ([API Guide](./api-guide.md)). You can only retrieve the features and process some of them in the console.

### Console Icons
Various forms of icons are used to provide information and features in the console.

![](../image/icons.png)

1. Details
2. Reupload
3. Navigation
4. Validation
5. Download
6. Import Process

### Export Request List

- You can make a query by applying query conditions.
    - Search key: You can make a query by using the search key sent when requesting to export.
    - Processing status
        - ALL: All
        - READY: Waiting for process
        - WORKING: Processing
        - COMPLETED: Completed
        - FAILED: Failed
- You can see the details of requests by clicking the Details icon.
- If uploading to storage fails, you can request upload again by clicking the Reupload icon.
    - If uploading to storage fails, a notification email will be sent to project members.

#### Details

- Details of the request can be found through scrolls.
    - Number of processed exports: You can check the number of processed exports requested. Large files over 10 KB are marked separately.
    - Expiration date: When uploading to a specified storage fails, the exported file is kept for 7 days and then deleted. You must request reupload before expiration date. (When uploading succeeds, it is immediately deleted.)
    - Password: A password specified upon request. You can release the exported fil with the specified password.
    - Storage information: Information on the storage specified when requesting. When you specify multiple storages, you can check them with the navigation icon.
    - Query parameter, extraction field, sheet: Additional information transmitted to the specified callback API URL upon request.

### Import Request List

- You can make a query by applying query conditions.
    - Search key: You can make a query by using the search key sent when requesting to import.
    - Processing status
        - ALL: All
        - FAILED: Failed
        - IMPORTED: Completed
        - IMPORTING: Processing
        - VALIDATED: Validation completed
        - VALIDATING: Validation in progress
        - READY: Waiting for process
- Requests including validation display the relevant icon.
- You can check the request detail by clicking the Details icon.
- For requests in the VALIDATED (Validation completed) status, the Download icon to download the success/failure result file is displayed.
- For requests in the VALIDATED (Validation completed) status, the Import Process icon is displayed.

#### Details

- You can find the request details.
    - Expiration date: Imported files and validation success and failure files are kept in 7 days and then deleted.
    - Password: When the file to be imported is encrypted and uploaded, File Crafter processes it using a password.
    - Validity check callback URL: A callback URL for validation.
    - Data start row: The row number where the actual data of the imported file starts. It is used in files with multi-line headers.
    - Auto Import process: After validation, the import operation continues without remaining in the VALIDATED status.
    - Processing result: You can find the processing result of the requested Import. Large files over 10 KB are marked separately.