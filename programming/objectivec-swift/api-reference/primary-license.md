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
  | [`initLicense`](#initlicense) | Initialize license for `DynamsoftBarcodeReader`. |
  
  ---

## initLicense

Initializes `DynamsoftBarcodeReader` with a license.

```objc
+ (void)initLicense:(nonnull NSString *)license verificationDelegate:(nonnull id<DBRLicenseVerificationListener>)listener 
NS_SWIFT_NAME(initLicense(_:verificationDelegate:));
```

**Parameters**

`[in] license` The license key.
`[in, out] verificationDelegate` The listener that handles callback when the license verification message is returned by the license server. See also [`DBRLicenseVerificationListener`](protocol-dbrlicenseverificationlistener.md).

**Return Value**

The instance of `DynamsoftBarcodeReader`.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[DynamsoftBarcodeReader initLicense:@"Put your license here" verificationDelegate: self];
- (void)DBRLicenseVerificationCallback:(bool)isSuccess error:(NSError *)error{
}
```
2. 
```swift
DynamsoftBarcodeReader.initLicense("Put your license here", verificationDelegate: self)
func dbrLicenseVerificationCallback(_ isSuccess: Bool, error: Error?) {
}
```
