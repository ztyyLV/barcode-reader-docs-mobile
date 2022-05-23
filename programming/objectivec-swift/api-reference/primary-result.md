---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Result Methods
description: This page shows Result methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: getIntermediateResult, result methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
---

# Result Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`getIntermediateResult`](#getintermediateresult) | Get intermediate results. |
  | [`enableResultVerification`](#enableresultverification) | Result will be verified before output. |
  | [`enableDuplicateFilter`](#enableduplicatefilter) | Duplicate results will be filtered and output only once for every 3 seconds |

  ---

## getIntermediateResult

Return intermediate results containing the original image, the color clustered image, the binarized image, contours, lines, text blocks, etc.

```objc
-(NSArray<iIntermediateResult*>* _Nullable)getIntermediateResult:(NSError* _Nullable *  _Nullable)error;
```

**Parameters**

`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

Returns an [`iIntermediateResult`](auxiliary-iIntermediateResult.md) array.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
iPublicRuntimeSettings *settings;
NSArray<iTextResult *> *result;
NSArray<iIntermediateResult *> *irResult;
[_barcodeReader getRuntimeSettings:nil];
settings.intermediateResultTypes = EnumIntermediateResultTypeColourConvertedGrayScaleImage|EnumIntermediateResultTypeOriginalImage|EnumIntermediateResultTypeColourClusteredImage;
[_barcodeReader updateRuntimeSettings:settings error:nil];
result = [_barcodeReader decodeFileWithName:@"your file path" error:nil];
irResult = [_barcodeReader getIntermediateResult:&error];
```
2. 
```swift
let settings = try? barcodeReader.getRuntimeSettings()
settings.intermediateResultTypes = EnumIntermediateResultType.ColourConvertedGrayScaleImage.rawValue | EnumIntermediateResultType.OriginalImage.rawValue | EnumIntermediateResultType.ColourClusteredImage.rawValue
barcodeReader.updateRuntimeSettings(settings)
let result = try? barcodeReader.decodeFileWithName("your file path", templateName:"")
let irResult = try? barcodeReader.getIntermediateResult()
```

## enableResultVerification

The text results will be verified before output if the result verification is enabled.

```objc
@property (nonatomic, assign) BOOL enableResultVerification;
```

**Parameters**

`boolean` value which stands for the target status of result verification mode.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader enableResultVerification:true];
// To check the status of this mode
[barcodeReader getEnableResultVerification]
```
2. 
```swift
barcodeReader.enableResultVerification = true
// To check the status of this mode
let x = barcodeReader.enableResultVerification
```

## enableDuplicateFilter

The duplicated text result will be filtered. The barcode reader will not output the result for the same barcode a second time if the second scan is within 3 seconds of the first.

```objc
@property (nonatomic, assign) BOOL enableDuplicateFilter;
```

**Parameters**

`boolean` value which stands for the target status of result duplicate filter mode.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader enableDuplicateFilter:true];
// To check the status of this mode
[barcodeReader getEnableDuplicateFilter]
```
2. 
```swift
barcodeReader.enableDuplicateFilter = true
// To check the status of this mode
let x = barcodeReader.enableDuplicateFilter
```
