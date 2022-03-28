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

  ---

## getIntermediateResult

Return intermediate results containing the original image, the color clustered image, the binarized image, contours, lines, text blocks, etc.

```objc
-(NSArray<iIntermediateResult*>* _Nullable)getIntermediateResult:(NSError* _Nullable *  _Nullable)error;
```

**Parameters**

`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

Returns intermediate result array.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
iPublicRuntimeSettings *settings;
NSError __autoreleasing * _Nullable error;
NSArray<iTextResult *> *result;
NSArray<iIntermediateResult *> *irResult;
[m_barcodeReader getRuntimeSettings:&error];
settings.intermediateResultTypes = EnumIntermediateResultTypeColourConvertedGrayScaleImage|EnumIntermediateResultTypeOriginalImage|EnumIntermediateResultTypeColourClusteredImage;
[m_barcodeReader updateRuntimeSettings:settings error:&error];
result = [m_barcodeReader decodeFileWithName:@"your file path" templateName:@"" error:&error];
irResult = [m_barcodeReader getIntermediateResult:&error];
```
2. 
```swift
let error: NSError? = NSError()
let settings = try? barcodeReader.getRuntimeSettings()
settings.intermediateResultTypes = EnumIntermediateResultType.ColourConvertedGrayScaleImage.rawValue | EnumIntermediateResultType.OriginalImage.rawValue | EnumIntermediateResultType.ColourClusteredImage.rawValue
barcodeReader.update(settings, error:nil)
let result = barcodeReader.decodeFileWithName("your file path", templateName:"", error:nil)
let irResult = barcodeReader.getIntermediateResult(&error)
```
