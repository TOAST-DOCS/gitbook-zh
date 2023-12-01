## Content Delivery > Image Manager > Release Notes

### November 1, 2023
#### Feature Updates
* [API] Added List Folder Default Properties API
* [Console] Removed folder size and number files from the folder properties
#### Bug Fixes
* [API] Fixed operation error for webp files
* [Console] Fixed an error where files are not uploaded even though they are an allowed extensions

### September 14, 2023
#### Feature Updates
* [API] Added supported file format (.webp)
* [API] Changed uploaded image size limit (12 MB > 50 MB)
* [API] Added the origial URL path to responses

### September 27, 2022
#### Service Name Change
* Changed the service name to Image Manager

### February 22, 2018
#### Feature Updates
* [Console] Changed the method of accessing 'Thumbnail Option Management' from a button within the 'Folder and Image File Management' to a top menu  
	* Folder and image file management is accessible from 'File View'
	* Thumbnail option management is accessible from 'Operation Setting'
* [Console] [Folder and Image File Management](./console-guide/#_1)
	* Added the feature of moving folder paths on the existing page, as well as the folder tree feature 
	* Added the feature of moving to a previous folder on the folder list

#### Bug Fixes 
* [API] Fixed a bug where, when sending a request with operation-exec API, the request is handled as a success response regardless of the task if the file (or operation) is invalid
	* Processed as a failed response when task items (queues) are unavailable 
	* Processed as a partial success response when task items (queues) count is not consistent with the request count 

### December 21, 2017 
#### Feature Updates
* [API] Added the display of whether the files have been overwritten to the processing result callback 
	* [Uploading Multiple Images](./api-guide/#_16)
	* [Executing Image Operations](./api-guide/#_37)
* [Console] Changed UI design of the page 

### November 30, 2017
#### More Features 
* [API] Added the processing result callback feature
	* Added the feature of sending processing result to callbackUrl when callbackUrl is sent as a parameter for an API call
		* [Uploading Multiple Images](./api-guide/#_16)
		* [Executing Image Operations](./api-guide/#_37)

#### Bug Fixes 
 * [Console] Fixed bugs in which an invalid subfolder path was created while uploading a folder including compression files 

### November 23, 2017
#### Feature Updates 
* [Added Features of Image Processing](./api-guide/#_25)
	* Added grid-split as part of splitting images
	* Added the watermark feature
* [Console] [Added Image Processing Option](./console-guide/#_10)
	* The option was available only for resizing but now is configurable as a common option  
		* Quality, image format, callback URL for result, whether to maintain meta data, whether to rotate based on orientation data  
	* Changed the default value for the option of maintaining GIF animation: Changed from Not Maintain to Maintain  
* [Console] [Grouping by image processing features](./console-guide/#_10)
	* Group 1 for Basic Processing: Resize, Gray, or Rectangle Crop
	* Group 2 for Split Processing: Slice Crop (width, height, grid)
	* Group 3 for Composite Processing : Circle Crop
	* Images are to be processed in the group sequence 
* [Console] [Changed Process of Product Closure](./console-guide/#_8)
	* Unable to close when there is a file left when stopping the use of the service
	* Added the feature to delete the whole files, and service use can be stopped after all files are deleted  

### May 25, 2017
#### Bug Fixes
* Fixed an error of parsing image meta information 

### April 20, 2017 
#### Feature Updates 
* [Added Thumbnail Resizing Method](./console-guide/#_10) 
    * Changed size to meet the width and height of option 
    * Changed standard size of the width of option
    * Changed standard size of the height of option 
* [Added the method of cropping](./console-guide/#_10)
    * Added Slice Crop 
* [Console] [Changed the option of maintaining Gif animation as global configuration](./console-guide/#_10)

#### Bug Fixes 
* Modified not to create a folder which includes a tilde

### March 23, 2017
#### Bug Fixes
* [Console] Fixed an issue in which Korean files uploaded on macOS were unable to be searched 
