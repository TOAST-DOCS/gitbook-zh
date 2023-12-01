## Content Delivery > Image Manager > Console User Guide

This document explains how to create folders, upload files, and manage thumbnail options using the console.

## Manage Folders and Image Files

You can manage folders, original image files, and created thumbnail image files on the **File View** screen of the menu.

![image_01_20220929](https://static.toastoven.net/prod_img/image_01_20220929.png)

### Toolbar Icon Description

![image_02_20220929](https://static.toastoven.net/prod_img/image_02_20220929.png)

### Create a Folder

![image_03_20220929](https://static.toastoven.net/prod_img/image_03_20220929.png)

1. A folder is the basic unit for storing images, and it is created by clicking the **Create Folder** button.

2. Enter a folder name and click **OK**.

   - A function to edit the name of a folder is not provided.
   - If you need to modify the name, you must delete the folder and re-create a folder.

### Upload Image Files

![image_04_20220929](https://static.toastoven.net/prod_img/image_04_20220929.png)

1. Select the desired folder to move into it, and click the **Upload** button.

   - You can upload multiple images at once, and you can also upload folders and compressed files.
   - When uploading a compressed file, the name of the folder within the compressed file must be at least two letters long.

2. Drag and drop image files, or click **Add Files** to select files to upload.

3. Select 'Overwrite' or 'Change Name' to handle files with the same name, and click **Upload**.

   - When the upload is completed normally, the screen is updated and you can check the file list.

### Download

![image_05_20220929](https://static.toastoven.net/prod_img/image_05_20220929.png)

1. After selecting a folder or image files to download, click the **Download** button.

2. If you select one image file after clicking the **OK** button, it will be downloaded immediately. If you select two or more files, the compressed file `nhn_cloud_image_manager.zip` will be downloaded.

   - You can only download up to 10,000 images at a time, and even if you download images stored in a folder, only 10,000 images can be downloaded in the same way.

### Delete Files or a Folder

![image_06_20220929](https://static.toastoven.net/prod_img/image_06_20220929.png)

1. After selecting the folder or image files to delete, click the **Delete** button.

2. Click **Confirm**.

   - If you select a folder, all files in that folder are also deleted.

### View Properties

![image_07_20231031](https://static.toastoven.net/prod_img/image_07_20231031.png)

Select one folder or image file and click the **Properties** button.

- If you select an image file, you can check the image's width and height, download URL, and meta information.

### Query and View the List

![image_08_20220929](https://static.toastoven.net/prod_img/image_08_20220929.png)

1. You can view files after filtering by the type of image file using 'View Filter'.

   - 'Original Image' means an image file uploaded directly through the console or API, and 'Created Thumbnail' means an image created by applying an operation to the original image.

2. Search for the image file name from the current location or from the entire location.

   - All results that contain a search term are retrieved, similar to `like '%search term%'` in the database.
   - Searches are case-sensitive.
      - Input example: sample
      - Example results: sample.gif, sample_2.gif, sample 3.gif, sample_sample_100x100.png

### Delete All Files

![image_09_20220929](https://static.toastoven.net/prod_img/image_09_20220929.png)

1. Click **Delete All Files**.

   - To terminate the use of the service, all files must be deleted.
   - A deleted file cannot be recovered, so use it with caution.

2. Click **Confirm**.

## Manage Thumbnail Options

![image_10_20220929](https://static.toastoven.net/prod_img/image_10_20220929.png)

Thumbnail options can be managed from the **Settings** screen of the menu.

You can generate thumbnails by a combination of several options.

### Create Thumbnails

![image_11_20220929](https://static.toastoven.net/prod_img/image_11_20220929.png)

1. Click **Add** to add thumbnail options.

2. Set name and description

   - Enter a name and description.
   - When there is the same option name, it is recommended to add a identifier after it.
   - For the description, enter a brief description of the thumbnail option for easy identification by users.

3. Set image processing options

   - Set image processing options.
   - Select the image generation quality and format.
   - In 'Callback URL', enter the address to be notified of the thumbnail generation result.
   - Select or clear the options 'Enable Real-time Processing', 'Maintain Image Meta Information', 'Rotate by Orientation', and 'Maintain GIF Animation'.
   - Circle Crop and Watermark, which are image composition, do not maintain the GIF animation effect.

4. Add image operation scenario

   - Click **+Add** to select image operation options.
   - Scenarios are run by group and the same option cannot be configured in duplicate.
   - Within the group, click the arrow button (▲▼) on the right side to set the scenario order.

![image_12_20220929](https://static.toastoven.net/prod_img/image_12_20220929.png)

The resizing of thumbnails are performed as follows.

- Change the size based on the longer side of Option: Perform resize while maintaining the ratio.
   - Example: If you resize a 400x300 image with the thumbnail size option 200x100, it will be resized to a 200x150 image.
- Change the size based on the shorter side of Option: Perform resize while maintaining the ratio.
   - Example: If you resize a 400x300 image with the thumbnail size option 200x100, it will be resized to a 133x100 image.
- Change the size to fit the width and height of Option: Perform resize to the configured size without maintaining the ratio.
   - Example: If you resize a 400x300 image with the thumbnail size option 200x100, it will be resized to a 200x100 image.
- Change the size based on the width of Option: Perform resize while maintaining the ratio.
   - Example: If you resize a 400x300 image with the thumbnail size option 200x100, it will be resized to a 200x150 image.
- Change the size based on the height of Option: Perform resize while maintaining the proportions.
   - Example: If you resize a 400x300 image with the thumbnail size option 200x100, it will be resized to a 133x100 image.

After completing the scenario settings, click **Save**.

### Edit Thumbnails

![image_13_20220929](https://static.toastoven.net/prod_img/image_13_20220929.png)

1. Select a thumbnail and click **Edit**.

2. Edit the thumbnail options and click **Edit**.

   - Even if you modify the options, the thumbnails created with the settings before modification are not modified.
   - If you check the 'Delete Operation Image' checkbox in the dialog box, you can bulk delete thumbnails created with the settings before modification.

### Delete Thumbnails

![image_14_20220929](https://static.toastoven.net/prod_img/image_14_20220929.png)

Click **Delete** to delete the thumbnail option.

- You can delete the selected thumbnail option with the Delete button.
- If you check the 'Delete Operation Image' checkbox in the dialog box, you can bulk delete thumbnails created with the operation.

### User Settings

![image_15_20220929](https://static.toastoven.net/prod_img/image_15_20220929.png)

1. Click **Setting**.

2. Choose to enable/disable real-time processing.
