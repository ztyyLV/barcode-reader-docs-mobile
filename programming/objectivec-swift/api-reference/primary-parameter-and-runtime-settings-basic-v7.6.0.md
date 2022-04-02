---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Parameter and Runtime Settings Basic Methods
description: This page shows basic Runtime Settings methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: setModeArgument, getModeArgument, getRuntimeSettings, updateRuntimeSettings, resetRuntimeSettings, parameter and runtime settings basic methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
---

# Objective-C API Reference - Parameter and Runtime Settings Basic Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`getRuntimeSettings`](#getruntimesettings) | Get current runtime settings. |
  | [`updateRuntimeSettings`](#updateruntimesettings) | Update runtime settings with a given struct. |
  | [`resetRuntimeSettings`](#resetruntimesettings) | Resets all parameters to default values. |

---

## getRuntimeSettings

Get current settings and save them into a [`iPublicRuntimeSettings`](../class/iPublicRuntimeSettings.md) struct.

```objc
- (iPublicRuntimeSettings* _Nullable)getRuntimeSettings:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return value**

A DBRPublicRuntimeSettings storing current runtime settings.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicense:@"t0260NwAAAHV***************"];
NSError __autoreleasing * _Nullable error;
[barcodeReader getRuntimeSettings:&error];
```
2. 
```swift
let error: NSError? = NSError()
let barcodeReader = DynamsoftBarcodeReader.init(license: "t0260NwAAAHV***************")
let licenseString = try? barcodeReader.getRuntimeSettings()
```

## updateRuntimeSettings

Update runtime settings with a given [`iPublicRuntimeSettings`](../class/iPublicRuntimeSettings.md) struct.

```objc
- (void)updateRuntimeSettings:(iPublicRuntimeSettings* _Nonnull)settings
                        error:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in] settings` The struct of template settings.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicense:@"t0260NwAAAHV***************"];
NSError __autoreleasing * _Nullable error;
iPublicRuntimeSettings *settings;
[barcodeReader updateRuntimeSettings:settings error:&error];
```
2. 
```swift
var error: NSError? = NSError()
let barcodeReader = DynamsoftBarcodeReader.init(license: "t0260NwAAAHV***************")
let settings = try? barcodeReader.getRuntimeSettings()
barcodeReader.update(settings, &error)
```

## resetRuntimeSettings

Reset all parameters to default values.

```objc
- (void)resetRuntimeSettings:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicense:@"t0260NwAAAHV***************"];
NSError __autoreleasing * _Nullable error;
[barcodeReader resetRuntimeSettings:&error];
```
2. 
```swift
var error: NSError? = NSError()
let barcodeReader = DynamsoftBarcodeReader.init(license: "t0260NwAAAHV***************")
barcodeReader.resetRuntimeSettings(&error)
```
