---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReaderException Class
description: This page shows the BarcodeReaderException Class of Dynamsoft Barcode Reader for Android SDK.
keywords: BarcodeReaderException, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
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

```java
try {
    //Do something here
} catch (BarcodeReaderException e) {
    e.printStackTrace();
}
```
