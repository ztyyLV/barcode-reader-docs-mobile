---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - General Settings Sample
description: This is the General Settings Sample page of Dynamsoft Barcode Reader for iOS SDK.
keywords: iOS, samples, General
needAutoGenerateSidebar: true
breadcrumbText: General Settings
---

# GeneralSettings Sample

This sample shows how to configure general barcode settings like the barcode formats, expected barcode count and the scan region when using Dynamsoft Barcode Reader iOS SDK.

**View Samples (on GitHub)**

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Objective-C/GeneralSettingsObjC/" target="_blank">Objective-C General Settings Sample</a>
- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Swift/GeneralSettingsSwift/" target="_blank">Swift General Settings Sample</a>

## Configure the Settings via PublicRuntimeSettings

### Barcode Format and Barcode Count Settings

The barcode formats settings and the barcode count settings are the most basic settings that determine the readability of your scan app. These parameters are all available for users to make changes through the class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html). To view all available barcode formats, please view the enumeration [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) and [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2).

**Code Snippet**

Objective-C:

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

Swift:

```swift
// General settings (including barcode format, barcode count and scan region) for the instance.
// Obtain current runtime settings of instance.
let settings = try? barcodeReader.getRuntimeSettings()
// Set the expected barcode format you want to read.
// The barcode format our library will search for is composed of BarcodeFormat group 1 and BarcodeFormat group 2.
// So you need to specify the barcode format in group 1 and group 2 individually.
settings!.barcodeFormatIds = EnumBarcodeFormat.ONED.rawValue | EnumBarcodeFormat.PDF417.rawValue | EnumBarcodeFormat.QRCODE.rawValue | EnumBarcodeFormat.DATAMATRIX.rawValue | EnumBarcodeFormat.AZTEC.rawValue
// Set the expected barcode count you want to read.
settings!.expectedBarcodesCount = 5
// Apply the new settings to the instance
barcodeReader.update(settings!, error: &error)
```

**Related APIs**

- Class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html)
- Enum [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat)
- Enum [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2)

### RegionDefinition - Set the Region

The scan region information is stored in [`RegionDefinition`]({{ site.oc_api }}auxiliary-iRegionDefinition.html) class. To set the scan region, you can make the region settings in class [`RegionDefinition`]({{ site.oc_api }}auxiliary-iRegionDefinition.html) and upload the settings through the class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html).

Please note, the orientation of the mobile frame is always Rotated 90 degrees counterclockwise from the orientation of your device. The following image illustrates the mobile frames' orientation.

<div align="center">
    <p><img src="assets/orientation-example.png" width="70%" alt="region"></p>
    <p>Region Orientation</p>
</div>

The **regionTop**, **regionBottom**, **regionLeft** and **regionRight** parameters in the class [`RegionDefinition`]({{ site.oc_api }}auxiliary-iRegionDefinition.html) stand for the region of frame but not the device. Therefore, please make sure that you are setting the correct parameters for the border of your scan region. For example, if you are going to create a scan region that margins 30% from the top and bottom of the frame. Actually, you have to set the **regionLeft** 30 to make the bottom of the scan region margin 30% from the top of the mobile screen.

**Code Snippet**

Objective-C:

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

Swift:

```swift
// General settings (including barcode format, barcode count and scan region) for the instance.
// Obtain current runtime settings of instance.
let settings = try? barcodeReader.getRuntimeSettings()
// Set the ROI(region of insterest) to speed up the barcode reading process.
// Note: DBR supports setting coordinates by pixels or percentages. The origin of the coordinate system is the upper left corner point.
// The int value 15 means the top of the scan region margins 15% from the top of screen.
settings!.region.regionTop      = 15 
settings!.region.regionBottom   = 85
settings!.region.regionLeft     = 30
settings!.region.regionRight    = 70
settings!.region.regionMeasuredByPercentage = 1
// Apply the new settings to the instance
barcodeReader.update(settings!, error: &error)
```

<div align="center">
    <p><img src="assets/dbr-region.png" width="70%" alt="region"></p>
    <p>How to Configure the Scan Region</p>
</div>

**Related APIs**

- Class [`RegionDefinition`]({{ site.oc_api }}auxiliary-iRegionDefinition.html)
- Class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html)

## Configure the Settings via JSON Template

Besides using the [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html) class, you can also upload the general barcode settings from stringified JSON data or a JSON file.

### Update the Runtime Settings via JSON String

Use method [`initRuntimeSettingsWithString`]({{ site.oc_api }}primary-parameter-and-runtime-settings-advanced.html#initruntimesettingswithstring) to upload the settings via a JSON string.

**Code Snippet**

Objective-C:

```objc
NSString* json = @"{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}";
[_barcodeReader initRuntimeSettingsWithString:json conflictMode:EnumConflictModeOverwrite error:&error];
```

Swift:

```swift
let json = "{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}"
barcodeReader.initRuntimeSettings(with: json, conflictMode: .overwrite, error: &error)
```

### Update the Runtime Settings via JSON File

Use method [`initRuntimeSettingsWithFile`]({{ site.oc_api }}primary-parameter-and-runtime-settings-advanced.html#initruntimesettingswithfile) to upload the settings via a JSON file.

**Code Snippet**

Objective-C:

```objc
NSError *error = [[NSError alloc] init];
// The method will overwrite the settings if the settings already exist.
[barcodeReader initRuntimeSettingsWithFile:@"your template file path" conflictMode:EnumConflictModeOverwrite error:&error];
```

Swift:

```swift
var error: NSError? = NSError()
// The method will overwrite the settings if the settings already exist.
barcodeReader.initRuntimeSettingsWithFile(fileName:"your template file path", conflictMode:EnumConflictMode.overwrite, error:&error)
```
