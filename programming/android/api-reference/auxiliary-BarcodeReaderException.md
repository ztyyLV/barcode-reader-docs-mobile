---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReaderException Class
description: This page shows the BarcodeReaderException Class of Dynamsoft Barcode Reader for Android SDK.
keywords: BarcodeReaderException, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---


# Class BarcodeReaderException

```java
import com.dynamsoft.dbr.BarcodeReaderException;
```

Exception for signalling barcode reader errors.
  
| Method | Type | Description |
|--------|------|-------------|
| [`getErrorCode`](#geterrorcode)| *int* | Get the error code |

## getErrorCode

**Return Value**

This method returns the DBR error code. Please view more about the error code in [`EnumErrorCode`]({{site.enumerations}}error-code.html)

**Code Snippet**

```java
try {
    //Do something here
} catch (BarcodeReaderException e) {
    e.printStackTrace();
}
```
