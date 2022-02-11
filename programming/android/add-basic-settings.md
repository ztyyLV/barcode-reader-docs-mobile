---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - Advanced Usage
description: This is the Advanced Usage page of Dynamsoft Barcode Reader for iOS SDK.
keywords: Guide, iOS, Settings
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# Quick Setup -- Basic Settings

If you have followed the guide in [Getting started](#user-guide.md), you have created a simplest video streaming barcode reader. On this page, you can learn about how to add basic settings for your barcode reader.

## Specify Barcode Formats

Specify the barcode format is always the first step of barcode reader configuration. Be sure to confirm that the targeting barcode formats are all included when configuring the barcode reader settings. Exclude the uninterest barcodes will also improve the processing efficiency. If you are not expert on recognizing barcode formats, the <a href="https://www.dynamsoft.com/barcode-types/barcode-types/" target="_blank">introduction of barcode formats</a> may help you understand the barcode formats. Generally, the barcode format settings are updated via `PublicRuntimeSettings` class by specifying enumeration member of `BarcodeFormat` or `BarcodeFormat_2`.

```java
// Create an instance of PublicRuntimeSettings.
// You can update basic settings via PublicRuntimeSettings class.
PublicRuntimeSettings settings = reader.getRuntimeSettings();

// Specify the barcode formats by enumeration values.
// The first group of barcode format (barcodeFormatIds) contains the majority of common barcode formats.
// Some special formats are listed in the second group (BarcodeFormatIds_2).
settings.barcodeFormatIds = EnumBarcodeFormat.BF_QR_CODE | EnumBarcodeFormat.BF_ONED;

// Update the configured settings.
reader.updateRuntimeSettings(settings);
```

## Set Barcode Count

The `expectedBarcodeCount` is the parameter that controls how many barcodes you would like the barcode reader to recognize from a single image. The process will be stopped as soon as the count of successfully decoded barcodes reaches the expected number.

There are some suggestions on how to set the `expectedBarcodeCount`:

- When the barcode reader is confirmed to focus on decoding single barcode, the recommended `expectedBarcodeCount` is 1. This will sharply improve the processing speed.
- When there are **n** barcodes in a single image (**n** is a fixed number) and you'd like the barcode reader to decode all of them, the recommended `expectedBarcodeCount` is **n**.
- When the count of targeting barcodes is unknown and you want to out put as many barcode results as possible, you can set the `expectedBarcodeCount` to the maximum possible count.
- When the count of targeting barcodes is unknown and you want to out put at least one barcode result as soon as possible, you can set the `expectedBarcodeCount` to 0. The barcode reader will try to decode at least one barcode from the image.

```java
PublicRuntimeSettings settings = reader.getRuntimeSettings();

// Set the expected barcode count
settings.expectedBarcodesCount = 0;
reader.updateRuntimeSettings(settings);
```

## Set Scan Region

It is not always necessary to scan the whole image to get the barcode result. You can set a scan region for your barcode reader when scanning a small-sized barcode on an image.

```java
RegionDefinition scanRegion = new RegionDefinition();
scanRegion.regionTop = 30;
scanRegion.regionBottom = 70;
scanRegion.regionRight = 15;
scanRegion.regionLeft = 85;
scanRegion.regionMeasuredByPercentage = 1;
try {
    mCameraEnhancer.setScanRegion(scanRegion);
} catch (CameraEnhancerException e) {
    e.printStackTrace();
}
```

The above settings are enough for the majority of usage scenarios. However, if the performance is still not satisfying, the following articles will help you on improving the performance.
