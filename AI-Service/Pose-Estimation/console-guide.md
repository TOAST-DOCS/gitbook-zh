## AI Service > Pose Estimation > Console User Guide

You can upload an image file to the console to recognize any human region and get information about the position of human joints in that region.

## Pose Estimation

### Upload an Image for Analysis

Upload an image to analyze.

- Images can be uploaded in the following two methods:
    1. Click the **Upload Image** button
    2. Drag and drop the image

### Analysis

After uploading the image, click the **Analyze** button and the analysis results will appear in JSON on the right side of the screen.

* [fileType] File extension (.jpg, .png)
* [numberOfPerson] The number of people recognized.
* [keyPointList] List of recognized people
    * [personId] ID assigned to distinguish recognition results
    * [inferKeypointList] List of recognized body parts
        * [name] Body part name
        * [part] The name of the part the body part belongs to (body, foot, face, hand)
        * [ x ] x coordinate
        * [ y ] y coordinate
        * [score] Confidence in the recognition result


```json
{
  "fileType": "png",
  "numberOfPerson": 5,
  "keyPointList": [
    {
      "personId": "0",
      "inferKeypointList": [
        {
          "name": "nose",
          "part": "body",
          "x": 367.151489,
          "y": 79.552887,
          "score": 0.976
        },
        {
          "name": "left_eye",
          "part": "body",
          "x": 373.819214,
          "y": 73.5605469,
          "score": 0.985
        },
        ...
      ]
    },
    ...
    {
      "personId": 2,
      "inferKeypoints": [
        {
          "name": "nose",
          "part": "body",
          "x": 98.7361755,
          "y": 68.2939758,
          "score": 0.979
        },
        {
          "name": "left_eye",
          "part": "body",
          "x": 110.171448,
          "y": 56.0753479,
          "score": 0.983
        },
        ...
      ]
    },
  ]
}
```

* Provides a feature to copy and download (in JSON) analysis results.
