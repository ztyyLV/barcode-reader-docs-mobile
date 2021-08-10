---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Interface DBRServerLicenseVerificationListener
description: This is the interface DBRServerLicenseVerificationListener page of Dynamsoft Barcode Reader for Android SDK.
keywords: DBRServerLicenseVerificationListener, interface, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# DBRServerLicenseVerificationListener

The interface `DBRServerLicenseVerificationListener` includes methods for users to get Dynamsoft license server callback.

```java
interface com.dynamsoft.dbr.DBRServerLicenseVerificationListener
```

| Method | Description |
| ------ | ----------- |
| `licenseVerificationCallback` | The abstract method for users to get the license verification callback. |

## licenseVerificationCallback

```java
void licenseVerificationCallback(boolean var1, Exception var2);
```

**Parameters**

`isSuccess`: Whether the license verification was successful.
`error`: The error message from license server.

**Code Snippet**

```java
DBRServerLicenseVerificationListener licenseVerificationListener = new DBRServerLicenseVerificationListener() {
    @Override
    public void licenseVerificationCallback(boolean b, Exception e) {
        // Add your code
    }
};
```
