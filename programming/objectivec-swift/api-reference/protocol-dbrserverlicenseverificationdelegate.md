---
layout: default-layout
title: Dynamsoft Barcode Reader iOS API Reference - DBRServerLicenseVerificationDelegate
description: This page shows DBRServerLicenseVerificationDelegate protocol of Dynamsoft Barcode Reader for iOS SDK.
keywords: DBRServerLicenseVerificationDelegate, api reference, iOS
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# DBRServerLicenseVerificationDelegate

`DBRServerLicenseVerificationDelegate` is the interface to handle license verification callback when using `initWithLicenseFromServer`.

> Note:  
>  
> - `initWithLicenseFromServer` and `DBRServerLicenseVerificationDelegate` are deprecated and will be removed in 10.0 version release.  
> - Please use [`initLicense`](primary-license.md#initlicense) and [`DBRLicenseVerificationListener`](protocol-dbrlicenseverificationlistener.md) to initialize and verify the license for 9.x versions.

```objc
@protocol DBRServerLicenseVerificationDelegate <NSObject>
```

| Method | Type | Description |
| ------ | ---- | ----------- |
| `licenseVerificationCallback` | *required* | The method for users to add code for license verification. |

## licenseVerificationCallback

The method for users to add code for license verification.

```objc
@required
- (void)licenseVerificationCallback:(bool)isSuccess error:(NSError * _Nullable)error;
```

**Parameters**

`[in, out] isSuccess`: Whether the license verification was successful.  
`[in, out] error`: The error message from the license server.
