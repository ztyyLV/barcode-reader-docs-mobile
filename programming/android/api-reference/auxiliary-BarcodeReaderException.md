---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReaderException Class
description: This page shows the BarcodeReaderException Class of Dynamsoft Barcode Reader for Android SDK.
keywords: BarcodeReaderException, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---


# BarcodeReaderException

Exception for signalling barcode reader errors.

```java
class com.dynamsoft.dbr.BarcodeReaderException;
```

| Method | Type | Description |
|--------|------|-------------|
| [`getErrorCode`](#geterrorcode)| *int* | Get the error code |

## getErrorCode

**Return Value**

This method returns the DBR error code. Please view more about the error code in [`EnumErrorCode`]({{site.enumerations}}error-code.html)

**Code Snippet**

```java
try {
    //Here we use decodeFile as example.
    reader.decodeFile("Your file path","");
} catch (BarcodeReaderException e) {
    Log.i("Decode", "onCreate: The error code for decode file is: "+e.getErrorCode());
}
```
