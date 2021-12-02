---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - Performance Settings Sample
description: This is the Performance Settings Sample page of Dynamsoft Barcode Reader for Android SDK.
keywords: android, sample, Performance
needAutoGenerateSidebar: true
breadcrumbText: Performance Settings
---

# PerformanceSettings Sample

| Template | Description |
| -------- | ----------- |
| `DEFAULT` | The default template for DBR mobile editions. |
| `VIDEO_SINGLE_BARCODE` | The video streaming barcode scanning template for single barcode usage scenario. |
| `VIDEO_SPEED_FIRST` | The video streaming barcode scanning template for speed first usage scenario. |
| `VIDEO_READ_RATE_FIRST` | The video streaming barcode scanning template for read-rate first usage scenario. |
| `IMAGE_SPEED_FIRST` | The image barcode reading template for speed first usage scenario. |
| `IMAGE_READ_RATE_FIRST` | The image barcode reading template for read-rate first usage scenario. |

View the sample

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/Performance/SpeedFirstSettings" target="_blank">Java (Android) Speed-first Settings Sample</a>

## Parameter Parsing

**Expected Barcode Count**

Parameter `ExpectedBarcodesCount` is an int value that refers to how many barcodes you would like to decode from a single image or frame. The barcode reader will try to find as many barcodes as the `ExpectedBarcodesCount` number. Set the `ExpectedBarcodesCount` to 1 can maximize the processing speed of your program but limit the read rate at the same time.

**Barcode Formats**

Parameter `BarcodeFormatIds` and `BarcodeFormatIds_2` are int values that controls the recognizable barcode formats. The less formats you set, the higher speed your app will be.

**Scale Down Threshold**

The image/frame will be continuously scaled down until it is smaller than the `ScaleDownThreshold`. You can use this parameter to improve the processing speed but the read rate and accuracy will decline on decoding the small-module barcode.

**Time out**



**Deblur Modes**

The `DeblurModes` parameter enable the Barcode Reader to try different algorthm on processing the blurry barcodes. This parameter will benefits the read rate but reduce the processing speed. In addition, processing the blurry images might cause misreading.

## Single Barcode Performance

**Template**

- `VIDEO_SINGLE_BARCODE`

You can simply choose the single barcode temple to

## Speed First Performance

**Template**

- `VIDEO_SPEED_FIRST`
- `IMAGE_SPEED_FIRST`

### Other Settings

**Set Scan Region**

Reducing the scan region size is the most effective way to speed up the barcode reading. To reduce the scan region size, you can restrict the border of the scan region via [`PublicRuntimeSettings`]({{ site.android_api }}auxiliary-PublicRuntimeSettings.html) and [`RegionDefinition`]({{ site.android_api }}auxiliary-RegionDefinition.html) classes. Displaying the scan region on the UI can also guide the users to manually approach the barcode area.

<div align="center">
    <p><img src="assets/region-definition.png" width="70%" alt="region-def"></p>
    <p>Reduce the Size of Scan Area</p>
</div>

**Multi-Frame Confirmation**

When a barcode result has been decoded more than once within a short period of time, we can confirm it is a correct result and output it. However, if a barcode result has never been decoded a second time within a period of time, we consider it a misread result and discard it.

**Error-Prone Barcode Filter**

**Result Filter**

**Camera Enhancer Settings**
