---
layout: default-layout
title: Dynamsoft Barcode Reader iOS API Reference - DBRLicenseVerificationListener
description: This page shows DBRLicenseVerificationListener protocol of Dynamsoft Barcode Reader for iOS SDK.
keywords: DBRLicenseVerificationListener, api reference, iOS
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
pageStartVer: 9.0
---

# DBRLicenseVerificationListener

`DBRLicenseVerificationListener` is the protocol to handle license verification callback when using [`initLicense`](primary-license.md#initlicense).

```objc
@protocol DBRLicenseVerificationListener <NSObject>
```

| Method | Type | Description |
| ------ | ---- | ----------- |
| `DBRLicenseVerificationCallback` | *required* | The method for users to add code for license verification. |

## DBRLicenseVerificationCallback

The method for users to add code for license verification.

```objc
@required
- (void)DBRLicenseVerificationCallback:(bool)isSuccess error:(NSError * _Nullable)error;
```

**Parameters**

`[in, out] isSuccess`: Whether the license verification was successful.  
`[in, out] error`: The error message from the license server.
