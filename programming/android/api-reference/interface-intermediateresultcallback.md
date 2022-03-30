---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Interface IntermediateResultListener
description: This the interface IntermediateResultListener page of Dynamsoft Barcode Reader for Android SDK.
keywords: IntermediateResultListener, interface, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# IntermediateResultListener

`IntermediateResultListener` is the interface to handle callback when intermediate results are returned.

```java
interface com.dynamsoft.dbr.IntermediateResultListener
```

| Method | Description |
| ------ | ----------- |
| `intermediateResultCallback` | Represents the method to handle the intermediate result array returned by the library. |

## intermediateResultCallback

Represents the method to handle the intermediate result array returned by the library.

```java
void intermediateResultCallback(int frameID, ImageData imageData, IntermediateResult[] intermediateResult;
```

**Parameters**

`frameId`: The ID of the frame.  
`imageData`: The image data of the frame.  
`results`: The intermediate result of the frame.

**Code Snippet**

```java
IntermediateResultListener intermediateResultListener = new IntermediateResultListener() {
    @Override
    public void intermediateResultCallback(int frameID, ImageData imageData, IntermediateResult[] intermediateResult) {
        // Add your code
    }
};
```
