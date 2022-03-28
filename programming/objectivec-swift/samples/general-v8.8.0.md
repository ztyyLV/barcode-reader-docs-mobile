---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - General Settings Sample
description: This is the General Settings Sample page of Dynamsoft Barcode Reader for iOS SDK.
keywords: iOS, samples, General
needAutoGenerateSidebar: true
breadcrumbText: GeneralSettings
---

# GeneralSettings Sample

This sample shows how to configure general barcode settings like the barcode formats, expected barcode count and the scan region when using Dynamsoft Barcode Reader iOS SDK.

**View Samples (on GitHub)**

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/v8.8.0/ios/Objective-C/GeneralSettingsObjC/" target="_blank">Objective-C General Settings Sample</a>
- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/v8.8.0/ios/Swift/GeneralSettingsSwift/" target="_blank">Swift General Settings Sample</a>

## Configure the Settings via PublicRuntimeSettings

### Specify Barcode Format and Barcode Count

The barcode formats settings and the barcode count settings are the most basic settings that determine the readability of your scan app. These parameters are all available for users to make changes through the class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html). To view all available barcode formats, please view the enumeration [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) and [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2).

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
// General settings (including barcode format, barcode count and scan region) for the instance.
// Obtain current runtime settings of instance.
iPublicRuntimeSettings *settings = [_barcodeReader getRuntimeSettings:&error];
// Set the expected barcode format you want to read.
// The barcode format our library will search for is composed of BarcodeFormat group 1 and BarcodeFormat group 2.
// So you need to specify the barcode format in group 1 and group 2 individually.
settings.barcodeFormatIds = EnumBarcodeFormatONED | EnumBarcodeFormatPDF417 | EnumBarcodeFormatQRCODE | EnumBarcodeFormatDATAMATRIX | EnumBarcodeFormatAZTEC;
// Set the expected barcode count you want to read.
settings.expectedBarcodesCount = 5;
// Apply the new settings to the instance
[_barcodeReader updateRuntimeSettings:settings error:&error];
```
2. 
```swift
// General settings (including barcode format, barcode count and scan region) for the instance.
// Obtain current runtime settings of instance.
let settings = try? barcodeReader.getRuntimeSettings()
// Set the expected barcode format you want to read.
// The barcode format our library will search for is composed of BarcodeFormat group 1 and BarcodeFormat group 2.
// So you need to specify the barcode format in group 1 and group 2 individually.
settings.barcodeFormatIds = EnumBarcodeFormat.ONED.rawValue | EnumBarcodeFormat.PDF417.rawValue | EnumBarcodeFormat.QRCODE.rawValue | EnumBarcodeFormat.DATAMATRIX.rawValue | EnumBarcodeFormat.AZTEC.rawValue
// Set the expected barcode count you want to read.
settings.expectedBarcodesCount = 5
// Apply the new settings to the instance
barcodeReader.update(settings, error: &error)
```

**Related APIs**

- Class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html)
- Enum [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat)
- Enum [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2)

### Specify the Scan Region

The scan region information is stored in [`RegionDefinition`]({{ site.oc_api }}auxiliary-iRegionDefinition.html) class. To set the scan region, you can make the region settings in class [`RegionDefinition`]({{ site.oc_api }}auxiliary-iRegionDefinition.html) and upload the settings through the class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html).

Please note, when using your phone in **portrait mode** the orientation of the mobile frame is rotated 90 degrees counterclockwise from the orientation of your device. The following image illustrates the mobile frames' orientation based on the camera view, either portrait or landscape.

<div align="center">
    <p><img src="assets/regionViews.png" width="70%" alt="region"></p>
    <p>Camera View vs Frame View</p>
</div>

The **regionTop**, **regionBottom**, **regionLeft** and **regionRight** parameters in the class [`RegionDefinition`]({{ site.oc_api }}auxiliary-iRegionDefinition.html) stand for the region of **frame** not the camera view. Since the parameters are based on the frame view instead of the camera view, let's see how the parameters would look like in the camera view once we rotate the frame view **90 degrees clockwise**. This is what we get based on the last example:

<div align="center">
    <p><img src="assets/frame-orientation.png" width="70%" alt="region"></p>
    <p>Region Orientation in Portrait</p>
</div>

Therefore, please make sure that you are setting the correct parameters for the border of your scan region. Let's say that you are looking to create a scan region on mobile with the following values
```
regionTop = 30%
regionBottom = 70%
regionLeft = 15%
regionRight = 85%
```
Considering that these region parameters (not the values) have to be rotated 90 degrees clockwise, here is how the values would then be transposed onto the mobile portrait view followed by the corresponding code snippet for mobile:

<div align="center">
    <p><img src="assets/regionConfig-mobile.png" width="70%" alt="region"></p>
    <p>How to Configure the Scan Region</p>
</div>


**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
// General settings (including barcode format, barcode count and scan region) for the instance.
// Obtain current runtime settings of instance.
iPublicRuntimeSettings *settings = [_barcodeReader getRuntimeSettings:&error];
// Set the ROI(region of insterest) to speed up the barcode reading process.
// Note: DBR supports setting coordinates by pixels or percentages. The origin of the coordinate system is the upper left corner point.
// The int value 15 means the top of the scan region margins 15% from the top of screen.
settings.region.regionTop      = 15; 
settings.region.regionBottom   = 85;
settings.region.regionLeft     = 30;
settings.region.regionRight    = 70;
settings.region.regionMeasuredByPercentage = 1;
// Apply the new settings to the instance
[_barcodeReader updateRuntimeSettings:settings error:&error];
```
2. 
```swift
// General settings (including barcode format, barcode count and scan region) for the instance.
// Obtain current runtime settings of instance.
let settings = try? barcodeReader.getRuntimeSettings()
// Set the ROI(region of insterest) to speed up the barcode reading process.
// Note: DBR supports setting coordinates by pixels or percentages. The origin of the coordinate system is the upper left corner point.
// The int value 15 means the top of the scan region margins 15% from the top of screen.
settings.region.regionTop      = 15 
settings.region.regionBottom   = 85
settings.region.regionLeft     = 30
settings.region.regionRight    = 70
settings.region.regionMeasuredByPercentage = 1
// Apply the new settings to the instance
barcodeReader.update(settings, error: &error)
```

**Related APIs**

- Class [`RegionDefinition`]({{ site.oc_api }}auxiliary-iRegionDefinition.html)
- Class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html)

## Configure the Settings via JSON Template

Besides using the [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html) class, you can also upload the general barcode settings from stringified JSON data or a JSON file.

### Update the Runtime Settings via JSON String

Use method [`initRuntimeSettingsWithString`]({{ site.oc_api }}primary-parameter-and-runtime-settings-advanced.html#initruntimesettingswithstring) to upload the settings via a JSON string.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
NSString* json = @"{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}";
[_barcodeReader initRuntimeSettingsWithString:json conflictMode:EnumConflictModeOverwrite error:&error];
```
2. 
```swift
let json = "{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}"
barcodeReader.initRuntimeSettings(json, conflictMode: .overwrite, error: &error)
```

### Update the Runtime Settings via JSON File

Use method [`initRuntimeSettingsWithFile`]({{ site.oc_api }}primary-parameter-and-runtime-settings-advanced.html#initruntimesettingswithfile) to upload the settings via a JSON file.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
NSError *error = [[NSError alloc] init];
// The method will overwrite the settings if the settings already exist.
[barcodeReader initRuntimeSettingsWithFile:@"your template file path" conflictMode:EnumConflictModeOverwrite error:&error];
```
2. 
```swift
var error: NSError? = NSError()
// The method will overwrite the settings if the settings already exist.
barcodeReader.initRuntimeSettingsWithFile("your template file path", conflictMode:EnumConflictMode.overwrite, error:&error)
```
