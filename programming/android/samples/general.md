---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - General Settings Sample
description: This is the General Settings Sample page of Dynamsoft Barcode Reader for Android SDK.
keywords: android, samples, General
needAutoGenerateSidebar: false
breadcrumbText: General Settings
---

# Android GeneralSettings Sample

This sample shows how to configure general barcode settings like the barcode formats, expected barcode count and the scan region when using Dynamsoft Barcode Reader Android SDK.

**View Samples (on GitHub)**

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/GeneralSettings/" target="_blank">Java (Android) General Settings Sample</a>

## The Barcode Settings

The barcode formats settings and the barcode count settings are the most basic settings that determine the readability of your scan app. These parameters are all available for users to make changes through the class [`PublicRuntimeSettings`]({{ site.android_api }}auxiliary-PublicRuntimeSettings.html). To view all available barcode formats, please view the enumeration [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) and [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2).

**Code Snippet**

```java
// General settings (including barcode format, barcode count and scan region) for the instance.
// Obtain current runtime settings of instance.
PublicRuntimeSettings runtimeSettings = reader.getRuntimeSettings();
// Set the expected barcode format you want to read.
// The barcode format our library will search for is composed of BarcodeFormat group 1 and BarcodeFormat group 2.
// So you need to specify the barcode format in group 1 and group 2 individually.
runtimeSettings.barcodeFormatIds = EnumBarcodeFormat.BF_ONED | EnumBarcodeFormat.BF_PDF417 | EnumBarcodeFormat.BF_QR_CODE | EnumBarcodeFormat.BF_DATAMATRIX |EnumBarcodeFormat.BF_AZTEC;
runtimeSettings.barcodeFormatIds_2 = 0;
// Set the expected barcode count you want to read.
runtimeSettings.expectedBarcodesCount = 5;
// Apply the new settings to the instance
reader.updateRuntimeSettings(runtimeSettings);
```

**Related APIs**

- Class [`PublicRuntimeSettings`]({{ site.android_api }}auxiliary-PublicRuntimeSettings.html)
- Enum [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat)
- Enum [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2)

## RegionDefinition - Set the Region

The scan region information is stored in [`RegionDefinition`]({{ site.android_api }}auxiliary-RegionDefinition.html) class. To set the scan region, you can make the region settings in class [`RegionDefinition`]({{ site.android_api }}auxiliary-RegionDefinition.html) and upload the settings through the class [`PublicRuntimeSettings`]({{ site.android_api }}auxiliary-PublicRuntimeSettings.html).

Please note, the orientation of the mobile frame is always Rotated 90 degrees counterclockwise from the orientation of your device. The following image illustrates the mobile frames' orientation.

<div align="center">
    <p><img src="assets/orientation-example.png" width="70%" alt="region"></p>
    <p>Region Orientation</p>
</div>

The **regionTop**, **regionBottom**, **regionLeft** and **regionRight** parameters in the class [`RegionDefinition`]({{ site.android_api }}auxiliary-RegionDefinition.html) stand for the region of frame but not the device. Therefore, please make sure that you are setting the correct parameters for the border of your scan region. For example, if you are going to create a scan region that margins 30% from the top and bottom of the frame. Actually, you have to set the **regionLeft** 30 to make the bottom of the scan region margin 30% from the top of the mobile screen.

**Code Snippet**

```java
// General settings (including barcode format, barcode count and scan region) for the instance.
// Obtain current runtime settings of instance.
PublicRuntimeSettings runtimeSettings = reader.getRuntimeSettings();
RegionDefinition regionDefinition = new RegionDefinition();
// Set the ROI(region of insterest) to speed up the barcode reading process.
// Note: DBR supports setting coordinates by pixels or percentages. The origin of the coordinate system is the upper left corner point.
// The int value 15 means the top of the scan region margins 15% from the top of screen.
regionDefinition.regionTop = 15;
regionDefinition.regionBottom = 85;
regionDefinition.regionLeft = 30;
regionDefinition.regionRight = 70;
regionDefinition.regionMeasuredByPercentage = 1;
runtimeSettings.region = regionDefinition;
// Apply the new settings to the instance
reader.updateRuntimeSettings(runtimeSettings);
```

<div align="center">
    <p><img src="assets/dbr-region.png" width="70%" alt="region"></p>
    <p>How to Configure the Scan Region</p>
</div>

**Related APIs**

- Class [`RegionDefinition`]({{ site.android_api }}auxiliary-RegionDefinition.html)
- Class [`PublicRuntimeSettings`]({{ site.android_api }}auxiliary-PublicRuntimeSettings.html)

## Configure the Settings via JSON Template

Besides using the [`PublicRuntimeSettings`]({{ site.android_api }}auxiliary-iPublicRuntimeSettings.html) class, you can also upload the general barcode settings from stringified JSON data or a JSON file.

### Update the Runtime Settings via JSON String

Use method [`initRuntimeSettingsWithString`]({{ site.android_api }}primary-parameter-and-runtime-settings-advanced.html#initruntimesettingswithstring) to upload the settings via a JSON string.

**Code Snippet**

```java
reader.initRuntimeSettingsWithString("{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}", EnumConflictMode.CM_OVERWRITE);
```

### Update the Runtime Settings via JSON File

Use method [`initRuntimeSettingsWithFile`]({{ site.android_api }}primary-parameter-and-runtime-settings-advanced.html#initruntimesettingswithfile) to upload the settings via a JSON file.

**Code Snippet**

```java
// Overwrite the settings if the settings already exist.
reader.initRuntimeSettingsWithFile("your template file path", EnumConflictMode.CM_OVERWRITE);
```
