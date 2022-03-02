---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - Advanced Usage
description: This is the Advanced Usage page of Dynamsoft Barcode Reader for iOS SDK.
keywords: Guide, iOS, Settings
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# Add Basic Settings

If you have followed the [Getting started](#user-guide.md), you may have managed to create a video streaming barcode reader project. In this article, you can learn about how to add basic runtime settings to your barcode reader project.

## Specify Barcode Formats

Specifying the barcode format is always the first step of barcode reader configuration. Be sure to confirm that the target barcode formats are included. Meanwhile, excluding the undesired barcodes will improve the processing efficiency. If you are not familiar with barcode format, the <a href="https://www.dynamsoft.com/barcode-types/barcode-types/" target="_blank">introduction of barcode formats</a> may help you understand it. Generally, the barcode format settings are updated via `PublicRuntimeSettings` class by specifying enumeration member of `BarcodeFormat` or `BarcodeFormat_2`.

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

The `expectedBarcodeCount` is the parameter that controls the number of expected results of the recognized barcodes via barcode reader from a single image. The process will be stopped as soon as the count of successfully decoded barcodes reaches the expected amount.

There are some suggestions on how to set the `expectedBarcodeCount`:

- When your project is design for decoding **single** barcode, the recommended `expectedBarcodeCount` is **1**. This will sharply improve the processing speed.
- When there are **n** barcodes in a single image (**n** is a fixed number) and you'd like the barcode reader to decode **all of them**, the recommended `expectedBarcodeCount` is **n**.
- When the number of barcodes is unknown and you want to output **as many** barcode results as possible, you can set the `expectedBarcodeCount` to the **maximum possible count**.
- When the number of barcodes is unknown and you want to output **at least one** barcode result as soon as possible, you can set the `expectedBarcodeCount` to **0**. The barcode reader will try to decode at least one barcode from the image.

```java
PublicRuntimeSettings settings = reader.getRuntimeSettings();

// Set the expected barcode count
settings.expectedBarcodesCount = 0;
reader.updateRuntimeSettings(settings);
```

## Define a Scan Region

It is not always necessary to scan the whole image to get the barcode result. You can define a scan region for your barcode reader to narrow the searching region.

```java
import com.dynamsoft.dce.CameraEnhancer;

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

The above settings can meet the majority of usage scenarios. However, if the performance is still not satisfying, the following articles will help you on improving the performance.

- [Quick optimize performance](quick-performance-settings.md)

If you are facing license issues, the following pages might help you.

- [Licence Activation]({{ site.license_activation }})
