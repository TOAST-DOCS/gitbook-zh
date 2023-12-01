## Application Service > File Crafter > Overview

- File Crafter is a service that sends repetitive requests using files to specific API URLs or to receive API response results collected as a file. The service supports difficult and time consuming processing such as memory management and asynchronous flow management required for large-capacity processing.

### Characteristics

- You can send repetitive requests using files to specific API URLs or to receive API response results collected as a file.
- Provides and receives data in the desired file format.
- Files after export processing are uploaded to the storage specified by customers.

### Main Features

- File Import
    - Repeatedly sends data provided as a file in the desired format to the customer API for processing.

- File Export
    - Processes the results received by repeatedly calling the requested customer API into the desired file format and uploads to the customer storage.
    - If the result file size is too large and multiple files are created, the files are compressed before uploading.

- Retrieve Processing Status
    - Allows you to retrieve the Import/Export processing status upon customer request.

- Enables to process Excel files with a password

### Service Targets

- When you need to extract the results of repetitive API calls to a file
- When you need to process large input data repeatedly
- When you wish to bypass difficult and complex work such as memory management and asynchronous flow management to process large data