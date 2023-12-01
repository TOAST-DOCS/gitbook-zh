## Content Delivery > Image Manager > Overview

Image is a service that provides comprehensive functions for storing, editing, and transferring images used in the customer's service.

## Main Features

- Provides a RESTful API that can be used by applications.
- Provides functions to create multiple folders, upload multiple images, download multiple files, and delete multiple files.
- Allows you to create thumbnails of the desired size in real time simply by adding parameters to the original image file URL.
- HTTP and HTTPS protocols can be used for the image file URL.

## Supported Images 

- The image file formats supported by the Image Manager service are as follows:
	- bmp, tif, tiff, miff, gif, jpe, jpeg, jpg, jps, pjpeg, jng, mng, png
- The Image Manager service allows you to upload image files of up to 12 MB.

## Glossary

| Term | Description |
|---|---|
| AppKey | A key for which the NHN Cloud user's project and the product are matched one-to-one, and one appkey for Image Manager is issued per project. |
| Secret Key | A secret key issued along with the appkey. Authentication requires sending this value as the 'Authorization' key in the header of the HTTP request. <br/>The secret key must be processed on the server and must not be included in the web page and mobile app source code, so that it is not exposed to external users. <br/>If you regenerate a secret key in the console, the previously used secret key cannot be used. |
| Folder | A folder is a unit for storing images, and is similar to a folder in Windows or a directory in Linux. |
| Original image | An image file uploaded directly through the console or API. |
| Generated thumbnail | A thumbnail created by dynamically adding operation parameters to the image URL or through operation execution APIs. |
| Image operations | Options for creating thumbnails. You can create thumbnails using predefined operations. |
