## Content Delivery > Image Manager > API Guide

The guide describes APIs of the Image Manager service.


## Common API Information

### Prerequisites

- To use the API, you need AppKey and Secret Key.
- AppKey and Secret Key can be found in the "URL & Appkey" menu on the top of the console.

### Common Request Information

- To use the APIs, security key authentication is required.
- You must send requests by including the Secret Key in 'Authorization' of all API request headers.

[Request Header]

| Name | Value | Description |
|---|---|---|
| Authorization | {secretKey} | Security key issued from the console |

### Common Response Information

- The API responds with "200 OK" to all API requests. For more information on the response results, see Response Body Header.

[Success response body]

```
{
	"header": {
		"isSuccessful": true,
		"resultCode": 0,
		"resultMessage": "Success"
	}
}
```

[Failure response body]

```
{
	"header": {
		"isSuccessful": false,
		"resultCode": 404,
		"resultMessage": "Please check your API Url, HTTP Method."
	}
}
```


## Folder API

### Create Folder

- Creates a folder in the specified path.

#### Request

[URI]

| Method | URI |
|---|---|
| POST | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/folders |

[Request Body]

- Creates a folder named myfolder under the root folder.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X POST 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/folders' \
-H 'Authorization: {secretKey}' \
-H 'Content-Type: application/json' \
--data '{"path": "/myfolder"}'
```

[Field]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| path | String | Min. 2 characters, Max. 255 Bytes | Required |  | The absolute path of the folder to be created, and a parent folder is automatically created |

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"folder": {
		"id": "c337256d-b17e-42ce-9f63-a792a05ae0ef",
		"name": "myfolder",
		"path": "/myfolder",
		"isFolder": true,
		"updatedAt": "2015-09-02T10:27:15+0900"
	}
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| folder | Object | Folder information |
| folder.isFolder | boolean | Whether it is a folder or not |
| folder.id | String | Unique ID |
| folder.name | String | Folder name |
| folder.path | String | Absolute path of a folder |
| folder.updatedAt | DateTime | Last modified date |


### List Files in a Folder

- Retrieves a list of items under the specified path or a list including specific characters in the name.

#### Request

[URI]

| Method | URI |
|---|---|
| GET | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/folders |

[Request Body]

- Retrieves the folders and files under /myfolder.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X GET 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/folders?basepath=/myfolder' \
-H 'Authorization: {secretKey}'
```

[Options]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| basepath | String | Min. 2 characters, Max. 255 Bytes | Required |  | The entire path of a folder to retrieve |
| createdBy | String | 1 character | Optional |  | Target of the list query <br>(Space: all, <br>U: user uploaded image, <br>P: operation image) |
| name | String | Min. 2 characters, Max. 255 Bytes | Optional |  | Image name to search for |
| page | int | Min. 1 | Optional | 1 | Page number |
| rows | int | Min. 1, Max. 10,000 | Optional | 100 | Query count |
| sort | String | | Optional | name:asc | Sorting method (Sort criteria: name or date, sorting method: asc or desc) |

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"paging": {
		"page": 1,
		"rows": 100,
		"totalFolderCount": 1,
		"totalFileCount": 1
	},
	"folders": [
		{
		"isFolder": true,
		"id": "5b6ad839-a920-4b88-895d-64ffc3f4d89a",
		"name": "banner",
		"path": "/myfolder/banner",
		"updatedAt": "2016-02-26T15:57:06+0900"
		}
	],
	"files": [
		{
			"isFolder": false,
			"id": "69528a77-0cc2-4407-a83d-ea4aacbe207f",
			"url": "http://image.toast.com/aaaaaag/myfolder/toast.png",
			"name": "toast.png",
			"path": "/myfolder/toast.png",
			"bytes": 10173,
			"createdBy": "U",
			"updatedAt": "2016-02-26T15:57:14+0900",
			"operationId": "",
			"queues": []
			"imageProperty": {
				"width": 90,
				"height": 90,
				"createdAt": "2016-02-26T15:56:50+0900"
				"coordinate": {
					"lat": 0,
					"lng": 0
				}
			}
		}
	]
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| paging | Object | Paging information |
| paging.page | int | Requested page number |
| paging.rows | int | Requested query count |
| paging.totalFolderCount | long | Total number of folders |
| paging.totalFileCount | long | Total number of folders |
| folders | List | Folder list |
| folders[0].isFolder | boolean | Whether it is a folder or not |
| folders[0].id | String | Unique ID |
| folders[0].name | String | Folder name |
| folders[0].path | String | Absolute path of a folder |
| folders[0].updatedAt | DateTime | Last modified date |
| files | List | List of image files |
| files[0].isFolder | boolean | Whether it is a folder or not |
| files[0].id | String | Unique ID |
| files[0].url | String | URL of image service |
| files[0].name | String | Image Name |
| files[0].path | String | Absolute path of a folder |
| files[0].bytes | long | Image file size |
| files[0].createdBy | String | Image classification (U: user uploaded image, P: operation image) |
| files[0].updatedAt | DateTime | Last modified date |
| files[0].operationId | String | If createdBy === P, a referenced operation ID |
| files[0].queues | List | List of task information (not used in this API) |
| files[0].imageProperty | Object | Image properties |
| files[0].imageProperty.width | int | Horizontal size |
| files[0].imageProperty.height | int | Vertical size |
| files[0].imageProperty.coordinate | Object | GPS information |
| files[0].imageProperty.createdAt | DateTime | Date of shooting or creation |
| files[0].imageProperty.coordinate.lat | double | Latitude |
| files[0].imageProperty.coordinate.lng | double | Longitude |


### List Folder Properties

- Retrieves properties such as the folder ID, capacity, and number of files.
- Retrieving properties can be time consuming depending on the number of files in the folder. If you don't need to retrieve the number of files in a folder and their total size, use the **List Folder Default Properties**.

#### Request

[URI]

| Method | URI |
|---|---|
| GET | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/properties |

[Request Body]

- Retrieves the folder properties of myfolder.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X GET 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/properties?path=/myfolder' \
-H 'Authorization: {secretKey}'
```

[Options]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| path | String | Min. 2 characters, Max. 255 Bytes | Required |  | Absolute path of the folder to retrieve |

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"folder": {
		"isFolder": true,
		"id": "996dd430-5172-4178-86c9-0704e88b28e3",
		"name": "myfolder",
		"path": "/myfolder",
		"bytes": 64857,
		"totalFolderCount": 1,
		"totalFileCount": 2,
		"updatedAt": "2016-02-26T15:57:06+0900"
	}
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| folder | Object | Folder information |
| folder.isFolder | boolean | Whether it is a folder or not |
| folder.id | String | Unique ID |
| folder.name | String | Folder name |
| folder.path | String | Absolute path of a folder |
| folder.bytes | long | Folder size (byte) |
| folder.totalFolderCount | long | Total number of subfolders |
| folder.totalFileCount | long | Total number of subfiles |
| folder.updatedAt | DateTime | Last modified date |

### List Folder Default Properties

- Retrieves folder properties from the List Folder Properties API, excluding the size, number of files, and number folders.

#### Request

[URI]

| Method | URI                                                                                 |
|---|-------------------------------------------------------------------------------------|
| GET | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/properties/simple |

[Request Body]

- Retrieves the folder properties of myfolder.
- Changes {appKey} and {secretKey} to the values found in the console.

```
curl -X GET 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/properties/simple?path=/myfolder' \
-H 'Authorization: {secretKey}'
```

[Option]

| Name | Type | Valid Range | Required | Default | Description |
|---|---|---|---|---|---|
| path | String | Min. 2 characters, Max. 255 bytes | Required |  | Absolute path to the folder to be retrieved  |

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"folder": {
		"isFolder": true,
		"id": "996dd430-5172-4178-86c9-0704e88b28e3",
		"name": "myfolder",
		"path": "/myfolder",
		"updatedAt": "2016-02-26T15:57:06+0900"
	}
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| folder | Object |  |
| folder.isFolder | boolean | Whether it is a folder or not |
| folder.id | String | Unique ID |
| folder.name | String | Folder name |
| folder.path | String | Absolute path to the folder |
| folder.updatedAt | DateTime | Last modified date |

## Upload API

### Upload a File

- Uploads a single image file.

#### Request

[URI]

| Method | URI |
|---|---|
| PUT | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/images |

[Request Body]

- Uploads the sample.png image to the /myfolder folder.
- You must change {appKey} and {secretKey} to the values found in the console.
- Input the binary data of the image file.

```
curl -X PUT 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/images?path=/myfolder/sample.png&overwrite=true' \
-H 'Authorization: {secretKey}' \
-H 'Content-Type:application/octet-stream' \
--data-binary 'path/to/imageFile/@sample.png'
```

[Options]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| path | String | Min. 2 characters, Max. 255 Bytes | Required |  | File name of the absolute path to be created |
| overwrite | boolean |  | Optional | false | Whether to overwrite if the same name exists |
| autorename | boolean |  | Optional | false | If the same name exists, <br>whether to change the file name to "name(1).extension" format |
| operationIds | String List |  | Optional |  | List of image operation IDs (separated by commas) |

- If you request by adding an image operation ID, you can create an operation file with the options you want when uploading.
- Refer to [Image Operation API](./api-guide/#image-operation-api).

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"file": {
		"isFolder": false,
		"id": "9cf11176-045c-4708-8dbd-35633f029a91",
		"url": "http://image.toast.com/aaaaach/myfolder/sample.png",
		"name": "sample.png",
		"path": "/myfolder/sample.png",
		"bytes": 54684,
		"createdBy": "U",
		"updatedAt": "2016-02-26T16:38:34+0900",
		"operationId": "100x100",
		"imageProperty": {
			"width": 200,
			"height": 150,
			"createdAt": "2016-02-26T16:38:11+0900",
			"coordinate": {
				"lat": null,
				"lng": null
			}
		},
		"queues": [
			"queueId": "0256316c-7dcf-4940-975b-673afb62e8a3",
			"queueType": "image",
			"status": "W",
			"tryCount": 0,
			"queuedAt": "2016-02-26T16:38:11+0900",
			"operationId": "100x100",
			"url": "http://image.toast.com/aaaaach/myfolder/sample_100x100.png",
			"name": "sample_100x100.png",
			"path": "/myfolder/sample_100x100.png"
		],
	}
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| file | Object | Image file information |
| file.isFolder | boolean | Whether it is a folder or not |
| file.id | String | Unique ID |
| file.url | String | URL of image service |
| file.name | String | Image Name |
| file.path | String | Absolute path of an image |
| file.bytes | long | Image file size |
| file.createdBy | String | Image classification (U: user uploaded image, P: operation image) |
| file.updatedAt | DateTime | Last modified date |
| file.operationId | String | If createdBy === P, a referenced operation ID |
| file.imageProperty | Object | Image properties |
| file.imageProperty.width | int | Horizontal size |
| file.imageProperty.height | int | Vertical size |
| file.imageProperty.createdAt | DateTime | Date of shooting or creation |
| file.imageProperty.coordinate | Object | GPS information |
| file.imageProperty.coordinate.lat | double | Latitude |
| file.imageProperty.coordinate.lng | double | Longitude |
| file.queues | List | List of task information requested by operationIds |
| file.queues[0].queueId | String | Task unique ID |
| file.queues[0].queueType | String | Task classification (image: operation, delete: delete files and folders) |
| file.queues[0].status | String | Task status (W: Waiting, D: Completed, P: In-progress, F: Failed) |
| file.queues[0].tryCount | int | Number of retries |
| file.queues[0].queuedAt | DateTime | Task registration date |
| file.queues[0].operationId | String | Referenced operation ID |
| file.queues[0].url | String | URL of image service to be provided |
| file.queues[0].name | String | Name of the image to be created |
| file.queues[0].path | String | Absolute path of the image to be created |


### Upload Multiple Files

- Uploads multiple image files.
- You can also upload compressed files.

#### Request

[URI]

| Method | URI |
|---|---|
| POST | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/images |

[Request Body]

- Uploads the left.png and right.png images to the /myfolder/banner folder.
- You must change {appKey} and {secretKey} to the values found in the console.
- Delivers the files in the multipart/form-data format.

```
curl -X POST 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/images' \
-H 'Authorization: {secretKey}' \
-F 'params={"basepath": "/myfolder/banner", "overwrite": true, "operationIds":["100x100"]}' \
-F 'files=@left.png' \
-F 'files=@right.png'
```

[Field]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| files | multipart/form–data |  | Required |  | List of image files |
| params | String | A string in a json format | Required |  | Upload options |
| params.basepath | String | Min. 2 characters, Max. 255 Bytes | Required |  | Absolute path to upload |
| params.overwrite | boolean |  | Optional | false | Whether to overwrite if the same name exists |
| params.autorename | boolean |  | Optional | false | If the same name exists, <br>whether to change the file name to "name(1).extension" format |
| params.operationIds | String List |  | Optional |  | List of image operation IDs. <br>Creates an operation file with the option you want when uploading. <br>Refer to the API related to image operation |
| params.callbackUrl | String |  | Optional |  | Callback URL path to receive processing result. <br>If you write the id in a query string format, it will be delivered together when sending a callback. <br>Only supports port 80 and port 443 |

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"errors": [],
	"successes": [
		{
			"isFolder": false,
			"id": "5fa8ce52-d066-490c-85dd-f8cef181dd28",
			"url": "http://image.toast.com/aaaaach/myfolder/banner/left.png",
			"name": "left.png",
			"path": "/myfolder/banner/left.png",
			"bytes": 7322,
			"createdBy": "U",
			"updatedAt": "2016-02-26T16:56:50+0900",
			"operationId": "100x100",
			"imageProperty": {
				"width": 60,
				"height": 60,
				"createdAt": "2016-02-26T16:56:27+0900"
				"coordinate": {
					"lat": null,
					"lng": null
				}
			},
			"queues": [
				{
					"queueId": "bef1736f-6637-459e-ae10-ac0961ebf59c",
					"queueType": "image",
					"status": "W",
					"tryCount": 0,
					"queuedAt": "2016-02-26T16:56:29+0900",
					"operationId": "100x100",
					"url": "http://image.toast.com/aaaaach/myfolder/banner/left_100x100.png",
					"name": "left_100x100.png",
					"path": "/myfolder/banner/left_100x100.png"
				}
			]
		},
		{
			"isFolder": false,
			"id": "96f726bd-93e4-4f7c-ad55-56e85aa323a8",
			"url": "http://image.toast.com/aaaaach/myfolder/banner/right.png",
			"name": "right.png",
			"path": "/myfolder/banner/right.png",
			"bytes": 267801,
			"createdBy": "U",
			"updatedAt": "2016-02-26T16:56:51+0900",
			"operationId": "100x100",
			"imageProperty": {
				"width": 1440,
				"height": 2560,
				"createdAt": "2016-02-26T16:56:28+0900",
				"coordinate": {
					"lat": null,
					"lng": null
				}
			},
			"queues": [
				{
					"queueId": "6691a01a-4585-4e26-989c-8ef25dd627a0",
					"queueType": "image",
					"status": "W",
					"tryCount": 0,
					"queuedAt": "2016-02-26T16:56:29+0900",
					"operationId": "100x100",
					"url": "http://image.toast.com/aaaaach/myfolder/banner/right_100x100.png",
					"name": "right_100x100.png",
					"path": "/myfolder/banner/right_100x100.png"
				}
			]
		}
	]
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| errors | List | List of upload errors |
| errors[0].path | String | Absolute path of a file |
| errors[0].bytes | long | File size |
| errors[0].error | Object | Error information |
| errors[0].error.resultCode | int | Error Code |
| errors[0].error.resultMessage | String | Error message |
| successes | List | List of upload successes |
| successes[0].isFolder | boolean | Whether it is a folder or not |
| successes[0].id | String | Unique ID |
| successes[0].url | String | URL of image service |
| successes[0].name | String | Image Name |
| successes[0].path | String | Absolute path of an image |
| successes[0].bytes | long | Image file size |
| successes[0].createdBy | String | Image classification (U: user uploaded image, P: operation image) |
| successes[0].updatedAt | DateTime | Last modified date |
| successes[0].operationId | String | If createdBy === P, a referenced operation ID |
| successes[0].imageProperty | Object | Image properties |
| successes[0].imageProperty.width | int | Horizontal size |
| successes[0].imageProperty.height | int | Vertical size |
| successes[0].imageProperty.createdAt | DateTime | Date of shooting or creation |
| successes[0].imageProperty.coordinate | Object | GPS information |
| successes[0].imageProperty.coordinate.lat | double | Latitude |
| successes[0].imageProperty.coordinate.lng | double | Longitude |
| successes[0].queues | List | List of task information requested by operationIds |
| successes[0].queues[0].queueId | String | Task unique ID |
| successes[0].queues[0].queueType | String | Task classification (image: operation, delete: delete files and folders) |
| successes[0].queues[0].status | String | Task status (W: Waiting, D: Completed, P: In-progress, F: Failed) |
| successes[0].queues[0].tryCount | int | Number of retries |
| successes[0].queues[0].queuedAt | DateTime | Task registration date |
| successes[0].queues[0].operationId | String | Referenced operation ID |
| successes[0].queues[0].url | String | URL of image service to be provided |
| successes[0].queues[0].name | String | Name of the image to be created |
| successes[0].queues[0].path | String | Absolute path of the image to be created |

[Request Result Callback Body]

```
{
	"header": {
		"resultMessage": "Partial Success",
		"resultCode": 1,
		"isSuccessful": false
	},
	"id": "100",
	"successFiles": [
		{
			"id": "c4de7cec-ba9c-44fa-b1fc-93e2eb29ed10",
			"name": "image.jpg",
			"path": "/myfolder/image.jpg",
			"url": "http://image.toast.com/aaaaach/myfolder/image.jpg",
			"width": 546,
			"height": 304,
			"sizeByte": 105190,
			"overwritten": true,
			"updatedAt": "2017-11-28T14:30:14+0900"
		}
	],
	"failFiles": [
		{
			"name": "test.jpg",
			"path": "/myfolder/test.jpg",
			"sizeByte": 105190,
			"resultCode": 20010,
			"resultMessage": "There is same file name."
		},
		{
			"name": "big_size.jpg",
			"path": "/myfolder/big_size.jpg",
			"sizeByte": 12925663,
			"resultCode": 11004,
			"resultMessage": "It was exceed the max volume you can upload at once."
		}
	]
}
```



## Deletion API

### Single Deletion (synchronous)

- Deletes a single folder or file.

#### Request

[URI]

| Method | URI |
|---|---|
| DELETE | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/images/sync |

[Request Body]

- Deletes the file /myfolder/sample.png.
- You can check the ID of /myfolder/sample.png through "List Files in a Folder" API on the right menu.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X DELETE 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/images/sync?
fileId=9cf11176-045c-4708-8dbd-35633f029a91' \
-H 'Authorization: {secretKey}'
```

[Field]

- At least one of "folderId" and "fileId" must be used.

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| folderId | String | Max. 50 characters |  |  | ID of the folder to be deleted |
| fileId | String | Max. 50 characters |  |  | ID of the file to be deleted |
| includeThumbnail | boolean |  | Optional | false | Also deletes the operation file created by the file to be deleted |

#### Response

[Response Body]

```
{
	"header": {
		"isSuccessful": true,
		"resultCode": 0,
		"resultMessage": "Success"
	}
}
```

### Multiple Deletion (asynchronous)

- Deletes multiple folders and files.
- Actual deletion of data is processed asynchronously.
- The processing result can be checked through the [Query a Task](./api-guide/#query-a-task) API with the "queueId" received as a response.

#### Request

[URI]

| Method | URI |
|---|---|
| DELETE | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/images/async |

[Request Body]

- Deletes the files /myfolder/banner/left.png and /myfolder/banner/right.png.
- The file and folder ID can be found through [List Files in a Folder](./api-guide/#list-files-in-a-folder).
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X DELETE 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/images/async?
fileIds=5fa8ce52-d066-490c-85dd-f8cef181dd28,96f726bd-93e4-4f7c-ad55-56e85aa323a8' \
-H 'Authorization: {secretKey}'
```

[Field]

- At least one of "folderIds" or "fileIds" must be used as a required parameter.

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| folderIds | String | Max. 50 characters per ID |  |  | List of IDs of folders to be deleted (separated by commas) |
| fileIds | String | Max. 50 characters per ID |  |  | List of IDs of files to be deleted (separated by commas) |
| includeThumbnail | boolean |  | Optional | false | Also deletes the operation file created by the file to be deleted |

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"queue": {
		"tryCount": 0,
		"queueId": "f1d27571-84e1-4892-9261-7d46755d45cc",
		"queueType": "delete",
		"status": "W",
		"queuedAt": "2018-01-12T10:44:44+0900",
		"operationId": "",
		"url": "",
		"name": "",
		"path": ""
	}
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| queue | Object | Task information |
| queue.queueId | String | Task unique ID |
| queue.queueType | String | Task type (delete: Deletes a file or folder) |
| queue.status | String | Task status (W: Waiting, D: Completed, P: In-progress, F: Failed) |
| queue.tryCount | int | Number of retries |
| queue.queuedAt | DateTime | Task registration date |
| queue.operationId | String | Referenced operation ID |
| queue.url | String | URL of image service to be provided |
| queue.name | String | Name of the image to be created |
| queue.path | String | Absolute path of the image to be created |


## Image Operation API

- You can create various thumbnails with Image Operation API.
- Provides the thumbnail size, black and white filter, crop (Rectangle, Circle, and Slice), and watermark.

### Create and Modify an Image Operation

- Creates or modifies an operation for image processing.

#### Request

[URI]

| Method | URI |
|---|---|
| PUT | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/operations/{operationId} |

[Request Body]

- Creates or modifies a task named 100x100 that reduces the image size to 100x100 based on the length of the longer axis between width and height.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X PUT 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/operations/100x100' \
-H 'Authorization: {secretKey}' \
-H 'Content-Type: application/json' \
--data '{"description": "", "realtimeService": true, "data": [{"templateOperationId": "resize_max_fit",
"option": {"resizeType": "max_fit", "width": 100, "height": 100, "quality": 80,
"upDownSizeType": "downOnly"}}]}'
```

[Field]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| operationId | String | Min.1 character, Max. 20 characters, <br>English letter or number | Required |  | Name of the operation to be created or modified |
| description | String | Max. 30 characters | Optional |  | Operation description |
| realtimeService | boolean |  | Optional | true | Whether to provide a real-time service |
| deleteThumbnail | boolean |  | Optional | false | Whether to delete the thumbnails previously created by the operation |
| data | List |  | Optional |  | List of operation tasks |

[Data Option]

- Thumbnail size

```
{
	"templateOperationId": "resize_max_fit", 	// (required, value: resize_max_fit, resize_min_fit, resize_fix, resize_width_fit, resize_height_fit)
												// Underlying template ID
	"option": {
		"width": int, 							// (required) Horizontal size
		"height": int, 							// (required) Vertical size
		"quality": double, 						// (optional, default: 75, value: 1~100) quality
		"upDownSizeType": String, 				// (optional, default: downOnly, value: downOnly / upOnly / upDownAll)
												// Whether it is unable to enlarge and reduce beyond the original size
		"keepAnimation": boolean, 				// (optional, default: true) Whether to maintain the GIF animation
		"keepExif": boolean, 					// (optional, default: true) Whether to maintain the meta information
		"autoOrient": boolean, 					// (optional, default: false) Whether to rotate based on the orientation information
		"targetExtension": String 				// (optional, default: null) The output format (extension)
	}
}
```

- Black and white filter

```
{
	"templateOperationId": "gray", 		// (required) Underlying template ID
	"option": {  						// (required) No option
		"keepAnimation": boolean 		// (optional, default: true) Whether to maintain the GIF animation
	}
}
```

- Rectangle crop

```
{
	"templateOperationId": "rectangle",	// (required) Underlying template ID
	"option": {
		"gravity": String, 				// (optional, default: Center, value: NorthWest / North / NorthEast /
										// West / Center / East / SouthWest / South / SouthEast)
										// Base position
		"offsetX": int,					// (optional, default: 0) Base position is moved. Negative numbers indicate moving in the opposite direction
		"offsetY": int,					// (optional, default: 0) Base position is moved. Negative numbers indicate moving in the opposite direction
		"width": int, 					// (required) Horizontal size
		"height": int, 					// (required) Vertical size
		"keepAnimation": boolean 		// (optional, default: false) Whether to maintain the GIF animation
	}
}
```

- Circle crop

```
{
	"templateOperationId": "circle", 	// (required) Underlying template ID
	"option": {
		"gravity": String, 				// (optional, default: Center, value: NorthWest / North / NorthEast /
										// West / Center / East / SouthWest / South / SouthEast)
										// Base position
		"offsetX": int,					// (optional, default: 0) Base position is moved. Negative numbers indicate moving in the opposite direction
		"offsetY": int,					// (optional, default: 0) Base position is moved. Negative numbers indicate moving in the opposite direction
		"radius": int 					// (required) Radius
	}
}
```

- Slice crop: Horizontal and vertical split

```
{
	"templateOperationId": "slice",		// (required) Underlying template ID
	"option": {
		"sliceCropType": String, 		// (optional, default: "vertical") Slice method (vertical, horizontal)
		"sliceSize": int, 				// (optional, default: 0) Slice size
		"keepAnimation": boolean, 		// (optional, default: true) Whether to maintain the GIF animation
		"callbackUrl": string 			// (optional) The URL path to receive the processing result. Only supports port 80 and port 443
	}
}
```

- Slice crop: Grid split

```
{
	"templateOperationId": "grid", 		// (required) Underlying template ID
	"option": {
		"countX": int, 					// (Required) Number of horizontal splits
		"countY": int, 					// (Required) Number of vertical splits
										// When the split piece size is not an integer after the original size is divided by the number of splits,
										// the image can be divided by a number of splits that is lower than the previously set number of splits.
		"callbackUrl": string 			// (optional) The URL path to receive the processing result. Only supports port 80 and port 443
	}
}
```

- Watermark

```
{
	"templateOperationId": "watermark", // (required) Underlying template ID
	"option": {
		"gravity": String, 				// (optional, default: Center, value: NorthWest / North / NorthEast /
										// West / Center / East / SouthWest / South / SouthEast)
										// Base position
		"offsetX": int,					// (optional, default: 0) Base position is moved. Negative numbers indicate moving in the opposite direction
		"offsetY": int,					// (optional, default: 0) Base position is moved. Negative numbers indicate moving in the opposite direction
		"watermarkImagePath": String 	// (Required) The path of an image file to be synthesized
	}
}
```


#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"operation": {
	"appKey": {appKey},
	"operationId": "100x100",
	"description": "",
	"realtimeService": true,
	"updatedAt": "2016-02-26T17:42:27+0900",
	"jobTemplate": [
		{
			"templateOperationId": "resize_max_fit",
			"jobType": "ResizeJob",
			"option": {
				"resizeType": "max_fit",
				"width": 100,
				"height": 100,
				"quality": 80,
				"shrinkLargerOnly": false,
				"upDownSizeType": "downOnly",
				"keepAnimation": false,
				"keepExif": true,
				"autoOrient": true
			}
		}
	]
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| operation | Object | Operation information |
| operation.appKey | String | User AppKey |
| operation.operationId | String | Operation name |
| operation.description | String | Operation description |
| operation.realtimeService | boolean | Whether to provide a real-time service |
| operation.updatedAt | DateTime | Last modified date |
| operation.jobTemplate | List | List of operation tasks |
| operation.jobTemplate[0].templateOperationId | String | Underlying template ID |
| operation.jobTemplate[0].jobType | String | Operation task type |
| operation.jobTemplate[0].option | Object | Operation task content |

### List Image Operations

- Retrieves a list of image operations.

#### Request

[URI]

| Method | URI |
|---|---|
| GET | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/operations |

[Request Body]

- Retrieves a list of user's operations.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X GET 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/operations' \
-H 'Authorization: {secretKey}'
```

[Field]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| name | String | Max. 20 characters, <br>English letter or number | Optional |  | Operation name to search for (starting with a input value) |
| page | int | Min. 1 | Optional | 1 | Page number |
| rows | int | Max. 10,000 | Optional | 20 | Query count |
| sort | String |  | Optional | date:desc | Sorting method (Sort criteria: name or date, sorting method: asc or desc) |
| template | boolean |  | Optional | false | Target of the list query (true: default operation, false: user-created operation) |

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"paging": {
		"page": 1,
		"rows": 20,
		"totalCount": 1
	},
	"operations": [
		{
			"appKey": {appKey},
			"operationId": "100x100",
			"description": "",
			"realtimeService": true,
			"updatedAt": "2016-02-26T17:42:27+0900",
			"jobTemplate": [
				{
					"templateOperationId": "resize_max_fit",
					"jobType": "ResizeJob",
					"option": {
						"resizeType": "max_fit",
						"width": 100,
						"height": 100,
						"quality": 80,
						"shrinkLargerOnly": false,
						"upDownSizeType": "downOnly",
						"keepAnimation": false,
						"keepExif": true,
						"autoOrient": true
					}
				}
			]
		}
	]
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| paging | Object | Paging information |
| paging.page | int | Requested page number |
| paging.rows | int | Requested query count |
| paging.totalCount | long | Total number |
| operations | List | List of operations |
| operations[0].appKey | String | User AppKey |
| operations[0].operationId | String | Operation name |
| operations[0].description | String | Operation description |
| operations[0].realtimeService | boolean | Whether to use a real-time service |
| operations[0].updatedAt | DateTime | Last modified date |
| operations[0].jobTemplate | List | List of operation tasks |
| operations[0].jobTemplate[0].templateOperationId | String | Underlying template ID |
| operations[0].jobTemplate[0].jobType | String | Operation task type |
| operations[0].jobTemplate[0].option | Object | Operation task content |

### Detailed Query of Image Operations

- Retrieves the details of a specific image operation.

#### Request

[URI]

| Method | URI |
|---|---|
| GET | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/operations/{operationId} |

[Request Body]

- Retrieves the 100x100 operation.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X GET 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/operations/100x100' \
-H 'Authorization: {secretKey}'
```

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"operation": {
		"appKey": {appKey},
		"operationId": "100x100",
		"description": "",
		"realtimeService": true,
		"updatedAt": "2016-02-26T17:42:27+0900",
		"jobTemplate": [
			{
				"templateOperationId": "resize_max_fit",
				"jobType": "ResizeJob",
				"option": {
					"resizeType": "max_fit",
					"width": 100,
					"height": 100,
					"quality": 80,
					"shrinkLargerOnly": false,
					"upDownSizeType": "downOnly",
					"keepAnimation": false,
					"keepExif": true,
					"autoOrient": true
				}
			}
		]
	}
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| operation | Object | Operation information |
| operation.appKey | String | User AppKey |
| operation.operationId | String | Operation name |
| operation.description | String | Operation description |
| operation.realtimeService | boolean | Whether to provide a real-time service |
| operation.updatedAt | DateTime | Last modified date |
| operation.jobTemplate | List | List of operation tasks |
| operation.jobTemplate[0].templateOperationId | String | Underlying template ID |
| operation.jobTemplate[0].jobType | String | Operation task type |
| operation.jobTemplate[0].option | Object | Operation task content |

### Delete an Image Operation

- Deletes a specific image operation.

#### Request

[URI]

| Method | URI |
|---|---|
| DELETE | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/operations/{operationId} |

[Request Body]

- Deletes the 100x100 operation.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X DELETE 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/operations/100x100' \
-H 'Authorization: {secretKey}'
```

[Options]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| deleteThumbnail | boolean |  | Optional | false | Whether to delete the thumbnails previously created by the operation |

#### Response

[Response Body]

```
{
	"header": {
		"isSuccessful": true,
		"resultCode": 0,
		"resultMessage": "Success"
	}
}
```

### Execute Image Operations (asynchronous)

- Executes operations on the specified file to generate thumbnails.
- The processing result can be checked through the [Query a Task](./api-guide/#query-a-task) API with the "queueId" received as a response.

#### Request

[URI]

| Method | URI |
|---|---|
| POST | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/operations-exec |

[Request Body]

- Creates files to which the 100x100 operation option is applied with the original files /myfolder/left.png, /myfolder/right.png.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X POST 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/operations-exec' \
-H 'Authorization: {secretKey}' \
-H 'Content-Type: application/json' \
--data '{"basepath": "/myfolder", "operationIds": ["100x100"],
"filepaths": ["/myfolder/left.png", "/myfolder/right.jpg"]}'
```

[Field]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| basepath | String | Min. 2 characters, Max. 255 Bytes | Required |  | Absolute path of a folder that serves as a base |
| filepaths | String List |  | Required |  | List of folders and files in the absolute path to execute the operations on |
| operationIds | String List |  | Required |  | List of operation IDs to execute |
| callbackUrl | String |  | Optional |  | The URL path to receive the processing result. <br>If you write an id in a query string format, it is delivered together when sending the callback. <br>Only supports port 80 and port 443 |

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"paging": {
		"page": 1,
		"rows": 20,
		"totalCount": 1
	},
	"operations": [
		{
			"appKey": {appKey},
			"operationId": "100x100",
			"description": "",
			"realtimeService": true,
			"updatedAt": "2016-02-26T17:42:27+0900",
			"jobTemplate": [
				{
					"templateOperationId": "resize_max_fit",
					"jobType": "ResizeJob",
					"option": {
						"resizeType": "max_fit",
						"width": 100,
						"height": 100,
						"quality": 80,
						"shrinkLargerOnly": false,
						"upDownSizeType": "downOnly",
						"keepAnimation": false,
						"keepExif": true,
						"autoOrient": true
					}
				}
			]
		}
	],
	"queues": [
		{
			"queueId": "6691a01a-4585-4e26-989c-8ef25dd627a0",
			"queueType": "image",
			"status": "W",
			"tryCount": 0,
			"queuedAt": "2016-02-26T16:56:29+0900",
			"operationId": "100x100",
			"url": "http://alpha-image.toast.com/aaaaach/myfolder/banner/right_100x100.png",
			"name": "right_100x100.png",
			"path": "/myfolder/banner/right_100x100.png"
		}
	]
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| operations | List | List of operations to execute |
| operations[0].appKey | String | User AppKey |
| operations[0].operationId | String | Operation name |
| operations[0].description | String | Operation description |
| operations[0].realtimeService | boolean | Whether to provide a real-time service |
| operations[0].updatedAt | DateTime | Last modified date |
| operations[0].jobTemplate | List | List of operation tasks |
| operations[0].jobTemplate[0].templateOperationId | String | Underlying template ID |
| operations[0].jobTemplate[0].jobType | String | Task type |
| operations[0].jobTemplate[0].option | Object | Task content |
| queues | List | List of task information |
| queues[0].queueId | String | Task unique ID |
| queues[0].queueType | String | Task classification (image: operation, delete: delete files and folders) |
| queues[0].status | String | Task status (W: Waiting, D: Completed, P: In-progress, F: Failed) |
| queues[0].tryCount | int | Number of retries |
| queues[0].queuedAt | DateTime | Task registration date |
| queues[0].operationId | String | Referenced operation ID |
| queues[0].url | String | URL of image service to be provided |
| queues[0].name | String | Name of the image to be created |
| queues[0].path | String | Absolute path of the image to be created |

[Request Result Callback Body]

```
// fail sample
{
	"header": {
		"isSuccessful": false,
		"resultCode": 500201,
		"resultMessage": "Operation fail. "
	},
	"id": "100",
	"overwritten": false,
	"operationId": "100x100",
	"sourceFile": {
		"url": "http://image.toast.com/aaaaach/myfolder/banner/left.png",
		"name": "left.png",
		"path": "/myfolder/banner/left.png"
	}
}

// success sample
{
	"header": {
		"isSuccessful": true,
		"resultCode": 0,
		"resultMessage": "Success"
	},
	"id": "100",
	"overwritten": true,
	"operationId": "slice-v",
	"sourceFile": {
		"url": "http://image.toast.com/aaaaach/myfolder/banner/vertical.png",
		"name": "vertical.png",
		"path": "/myfolder/banner/vertical.png"
	},
	"resultFiles": [
		{
			"url": "http://image.toast.com/aaaaach/myfolder/banner/vertical_slice-v_0000.png",
			"name": "vertical_slice-v_0000.png",
			"path": "/myfolder/banner/vertical_slice-v_0000.png"
		},
		{
			"url": "http://image.toast.com/aaaaach/myfolder/banner/vertical_slice-v_0001.png",
			"name": "vertical_slice-v_0001.png",
			"path": "/myfolder/banner/vertical_slice-v_0001.png"
		}
	]
}
```


## Real-time Service API

### Query a Real-time Service

- Retrieves whether a user used the image operation real-time service.

#### Request

[URI]

| Method | URI |
|---|---|
| GET | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/users |

[Request Body]

- Retrieves a user’s real-time service.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X GET 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/users' \
-H 'Authorization: {secretKey}'
```

#### Response

[Response Body]

```
{
	"header": {
		// Omitted
	},
	"user": {
		"appKey": {appkey},
		"containerName": "aaaaach",
		"realtimeService": true
	}
}
```

[Field]

| Name | Value | Description |
|---|---|---|
| user | Object | User Information |
| user.appKey | String | User AppKey |
| user.containerName | String | User’s container information |
| user.realtimeService | boolean | Whether to provide a real-time service |


### Change a Real-time Service

- Changes whether a user used the image operation real-time service.

#### Request

[URI]

| Method | URI |
|---|---|
| PUT | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/users |

[Request Body]

- Changes a user’s real-time service.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X PUT 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/users' \
-H 'Authorization: {secretKey}' \
-H 'Content-Type: application/json' \
--data '{"realtimeService": false}'
```

[Field]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| realtimeService | boolean |  | Required |  | Whether to provide a real-time service |

#### Response

[Response Body]

```
{
	"header": {
		"isSuccessful": true,
		"resultCode": 0,
		"resultMessage": "Success"
	}
}
```


## Task API

### Query Task

- Retrieves the tasks of processing or deleting image operations.

#### Request

[URI]

| Method | URI |
|---|---|
| GET | https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appkey}/queues/{queueId} |

[Request Body]

- Retrieves the current status of an operation request.
- You must change {appKey} and {secretKey} to the values found in the console.

```
curl -X GET 'https://api-image.nhncloudservice.com/image/v2.0/appkeys/{appKey}/queues/6691a01a-4585-4e26-989c-8ef25dd627a0' \
-H 'Authorization: {secretKey}'
```

[Field]

| Name | Type | Valid range | Required | Default | Description |
|---|---|---|---|---|---|
| queueId | String | Max. 64 characters | Required |  | Task unique ID to search for |

#### Response

[Response Body]

```
{
	"header": {
		"isSuccessful": true,
		"resultCode": 0,
		"resultMessage": "Success"
	},
	"queue": {
		"queueId": "6691a01a-4585-4e26-989c-8ef25dd627a0",
		"queueType": "image",
		"status": "D",
		"tryCount": 0,
		"queuedAt": "2016-02-26T16:56:52+0900",
		"operationId": "100x100",
		"url": "http://image.toast.com/aaaaach/myfolder/banner/right_100x100.png",
		"name": "right_100x100.png",
		"path": "/myfolder/banner/right_100x100.png"
	}
}
```

[Field]

| Name | Type | Description |
|---|---|---|
| queue | Object | Task information |
| queue.queueId | String | Task unique ID |
| queue.queueType | String | Task classification (image: operation, delete: delete files and folders) |
| queue.status | String | Task status (W: Waiting, D: Completed, P: In-progress, F: Failed) |
| queue.tryCount | int | Number of retries |
| queue.queuedAt | DateTime | Task start date |
| queue.operationId | String | Referenced operation ID |
| queue.url | String | URL of image service that will be provided or has been provided |
| queue.name | String | Name of an image to be created (was created) |
| queue.path | String | Absolute path to the image that will be created or has been created |
