---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReader Status Retrieval Methods
description: This page shows BarcodeReader status retrieval methods of Dynamsoft Barcode Reader for Android SDK.
keywords: getVersion, status retrieval methods, BarcodeReader, api reference, android
needAutoGenerateSidebar: true
---

# Android API Reference - BarcodeReader Status Retrieval Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`getVersion`](#getversion) | Get version information of SDK.|

  ---

## getVersion

Get version information of SDK.

```java
String com.dynamsoft.barcode.BarcodeReader.getVersion()	
```

**Return value**

The version information string.

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
String versionInfo = reader.getVersion();
```
