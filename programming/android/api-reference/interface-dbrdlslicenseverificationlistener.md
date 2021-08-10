---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Interface DBRDLSLicenseVerificationListener
description: This is the interface DBRDLSLicenseVerificationListener page of Dynamsoft Barcode Reader for Android SDK.
keywords: DBRDLSLicenseVerificationListener, interface, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# DBRDLSLicenseVerificationListener

The interface `DBRDLSLicenseVerificationListener` includes methods for users to get Dynamsoft license server callback.

```java
interface com.dynamsoft.dbr.DBRDLSLicenseVerificationListener
```

| Method | Description |
| ------ | ----------- |
| `DLSLicenseVerificationCallback` | The abstract method for users to get the license server callback. |

## DLSLicenseVerificationCallback

```java
void DLSLicenseVerificationCallback(boolean var1, Exception var2);
```

**Parameters**

`isSuccess`: Whether the license verification was successful.
`error`: The error message from license server.

**Code Snippet**

```java
DBRDLSLicenseVerificationListener dbrDLSListener = new DBRDLSLicenseVerificationListener() {
    @Override
    public void DLSLicenseVerificationCallback(boolean b, Exception e) {
        // Add your code
    }
};
```
