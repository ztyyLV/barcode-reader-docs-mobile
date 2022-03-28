---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - General Settings Sample
description: This is the General Settings Sample page of Dynamsoft Barcode Reader for iOS SDK.
keywords: iOS, samples, General
needAutoGenerateSidebar: true
breadcrumbText: GeneralSettings
---

# GeneralSettings Sample

This sample shows the general barcode decoding settings and how to configure the settings via [`PublicRuntimeSettings`]({{ site.android_api }}auxiliary-iPublicRuntimeSettings.html) struct or JSON when using Dynamsoft Barcode Reader Android SDK.

**View the Sample(s)**

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Objective-C/GeneralSettingsObjC/" target="_blank">Objective-C General Settings Sample</a>
- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Swift/GeneralSettingsSwift/" target="_blank">Swift General Settings Sample</a>

## General Settings

**Barcode Formats & Expected Barcode Count**

The barcode formats settings and the barcode count settings are the most basic settings that determine the readability of your scan app. These parameters are all available for users to make changes through the class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html). To view all available barcode formats, please view the enumeration [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) and [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2).

**Scan Region**

For video barcode decoding scenarios, specifying a **scanRegion** can reduce the size of the processing area, which sharply increases the barcode decoding speed. To specify the scan region, you can use the **CameraEnhancer** method <a href="https://www.dynamsoft.com/camera-enhancer/docs/programming/ios/primary-api/camera-enhancer.html?ver=latest#setscanregion" target="_blank">`setScanRegion`</a>. When the **scanRegion** is configured via **CameraEnhancer**, the video frames will be cropped based on the **scanRegion** before being processed by the barcode reader.

## Update the Settings

### Via JSON Template

Besides using the [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html) class, you can also upload the general barcode settings from stringified JSON data or a JSON file.

#### From JSON String

Use method [`initRuntimeSettingsWithString`]({{ site.oc_api }}primary-parameter-and-runtime-settings-advanced.html#initruntimesettingswithstring) to upload the settings via a JSON string.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
NSString* json = @"{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}";
[_barcodeReader initRuntimeSettingsWithString:json conflictMode:EnumConflictModeOverwrite error:nil];
```
2. 
```swift
let json = "{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}"
try? barcodeReader.initRuntimeSettingsWithString(json, conflictMode: .overwrite)
```

#### From JSON File

Use method [`initRuntimeSettingsWithFile`]({{ site.oc_api }}primary-parameter-and-runtime-settings-advanced.html#initruntimesettingswithfile) to upload the settings via a JSON file.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
// The method will overwrite the settings if the settings already exist.
[barcodeReader initRuntimeSettingsWithFile:@"your template file path" conflictMode:EnumConflictModeOverwrite error:nil];
```
2. 
```swift
// The method will overwrite the settings if the settings already exist.
try? barcodeReader.initRuntimeSettingsWithFile("your template file path", conflictMode:EnumConflictMode.overwrite)
```

**Related APIs**

- Class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html)
- Enum [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat)
- Enum [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2)
