---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Initialize Methods
description: This page shows Initialize methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: init, initialize methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
---


# Initialize Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`init`](#init) | Create an instance of Dynamsoft Barcode Reader. |
  
  ---

## init

Initializes DynamsoftBarcodeReader.

```objc
- (instancetype _Nonnull)init;
```

**Return Value**

The instance of DynamsoftBarcodeReader.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
BarcodeReader = [[DynamsoftBarcodeReader alloc] init];
```
2. 
```swift
let barcodeReader = DynamsoftBarcodeReader.init()
```

**Remarks**

Partial of the decoding result will be masked with "*" without a valid license key.

## dispose

Destroy the instance of Dynamsoft Barcode Reader.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader dispose];
```
2. 
```swift
barcodeReader.dispose()
```
