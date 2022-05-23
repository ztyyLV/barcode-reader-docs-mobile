---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Interface TextResultListener
description: This the interface TextResultListener page of Dynamsoft Barcode Reader for Android SDK.
keywords: TextResultListener, interface, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# TextResultListener

`TextResultListener` is the interface to handle callbacks when the barcode results are returned.

```java
interface com.dynamsoft.dbr.TextResultListener
```

| Method | Description |
| ------ | ----------- |
| `textResultCallback` | Represents the method to handle the text result array returned by the library. |

## textResultCallback

Represents the method to handle the text result array returned by the library.

```java
void textResultCallback(int frameId, ImageData imageData, TextResult[] results);
```

**Parameters**

`frameId`: The ID of the frame.  
`imageData`: The image data of the frame.  
`results`: Recognized barcode results of the frame.

**Code Snippet**

You must use the video barcode decoding method to get the text result callback. You can view detailed code snippets about the usage of `textResultCallback` in the [Video Method](primary-video.md#setcameraenhancer) section.
