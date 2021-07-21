---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReader Status Retrieval Methods
description: This page shows BarcodeReader status retrieval methods of Dynamsoft Barcode Reader for Android SDK.
keywords: getVersion, status retrieval methods, BarcodeReader, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
---

# Status Retrieval Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`getVersion`](#getversion) | Get version information of SDK.|

  ---

## getVersion

Get version information of SDK.

```java
String com.dynamsoft.dbr.BarcodeReader.getVersion()
```

**Return value**

The version information string.

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
DMDLSConnectionParameters info = new DMDLSConnectionParameters();
info.organizationID = "200001";
info.sessionPassword = "******";
reader.initLicenseFromDLS(info, new DBRDLSLicenseVerificationListener() {
   @Override
   public void DLSLicenseVerificationCallback(boolean b, Exception e) {
      if (!b && e != null) {
         e.printStackTrace();
      }
   }
});
String versionInfo = reader.getVersion();
reader.destroy();
```
