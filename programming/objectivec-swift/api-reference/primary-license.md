---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - License Methods
description: This page shows License methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: initWithLicense, initWithLicenseFromServer, outputLicenseToString, license methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
---

# License Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`license`](#license) | Stores the license used in DynamsoftBarcodeReader. |
  ---

## initLicense

Initializes DynamsoftBarcodeReader with a license.

```objc
- (instancetype _Nonnull)initLicense:(NSString* _Nonnull)license;
```

**Parameters**

`[in] license` The license key.

**Return Value**

The instance of DynamsoftBarcodeReader.

**Code Snippet**

Objective-C:

```objc
[DynamsoftBarcodeReader initLicense:@"Put your license here" verificationDelegate: self];

- (void)DBRLicenseVerificationCallback:(bool)isSuccess error:(NSError *)error{
}
```

Swift:

```Swift
DynamsoftBarcodeReader.initLicense("Put your license here", verificationDelegate: self)

func dbrLicenseVerificationCallback(_ isSuccess: Bool, error: Error?) {
}
```
