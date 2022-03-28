---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Camera Methods
description: This page shows Camera methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: getIntermediateResult, Camera methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
pageStartVer: 8.2.1
---

# Camera Enhancer Methods

> Note:  
>  
> - Camera Enhancer methods are removed in 9.0 version. Please use the [video methods](primary-video.md) for video barcode scanning if you are using the latest version.

| Method | Description |
|--------|-------------|
| [`SetCameraEnhancerParam`](#setcameraenhancerparam) | Set the parameters for Dynamsoft Camera Enhancer in Barcode reader |

This page illustrates the controlling of `Dynamsoft Camera Enhancer`. To get a better understanding of this section, please read more about [`Dynamsoft Camera Enhancer`](https://www.dynamsoft.com/camera-enhancer/docs/introduction/?ver=latest){:target="_blank"}.

## SetCameraEnhancerParam

Set the callback parameters for Camera Enhancer

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
iDCESettingParameters* para = [[iDCESettingsParameters alloc] init];
para.cameraInstance = _dce;
para.textResultDelegate = self;
[_barcodeReader setCameraEnhancerPara:para];
```
2. 
```swift
let para = iDCESettingParameters.init()
para.cameraInstance = dce
para.textResultDelegate = self
barcodeReader.setCameraEnhancerPara(para)
```
