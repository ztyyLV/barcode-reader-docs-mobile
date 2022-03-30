---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Interface DBRLicenseVerificationListener
description: This is the interface DBRLicenseVerificationListener page of Dynamsoft Barcode Reader for Android SDK.
keywords: DBRLicenseVerificationListener, interface, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
pageStartVer: 9.0
---

# DBRLicenseVerificationListener

`DBRLicenseVerificationListener` is the interface to handle callback when using [`initLicense`](primary-license.md#initlicense).

```java
interface com.dynamsoft.dbr.DBRDLSLicenseVerificationListener
```

| Method | Description |
| ------ | ----------- |
| `DBRLicenseVerificationCallback` | The callback of license server. |

## DBRLicenseVerificationCallback

```java
void DBRLicenseVerificationCallback(boolean isSuccess, Exception error);
```

**Parameters**

`isSuccess`: Whether the license verification was successful.  
`error`: The error message from license server.

**Code Snippet**

```java
DBRLicenseVerificationListener dbrLicenseListener = new DBRLicenseVerificationListener() {
    @Override
    public void DBRLicenseVerificationCallback(boolean isSuccess, Exception error) {
        // Add your code
    }
};
```
