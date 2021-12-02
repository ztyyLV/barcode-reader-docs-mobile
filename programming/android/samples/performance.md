---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - Performance Settings Sample
description: This is the Performance Settings Sample page of Dynamsoft Barcode Reader for Android SDK.
keywords: android, sample, Performance
needAutoGenerateSidebar: true
breadcrumbText: Performance Settings
---

# PerformanceSettings Sample

View the sample

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/Performance/SpeedFirstSettings" target="_blank">Java (Android) Speed-first Settings Sample</a>

## Templates

| Template | Description |
| -------- | ----------- |
| `DEFAULT` | The default template for DBR mobile editions. |
| `VIDEO_SINGLE_BARCODE` | The video streaming barcode scanning template for single barcode usage scenario. |
| `VIDEO_SPEED_FIRST` | The video streaming barcode scanning template for speed first usage scenario. |
| `VIDEO_READ_RATE_FIRST` | The video streaming barcode scanning template for read-rate first usage scenario. |
| `IMAGE_SPEED_FIRST` | The image barcode reading template for speed first usage scenario. |
| `IMAGE_READ_RATE_FIRST` | The image barcode reading template for read-rate first usage scenario. |

## Parameter Parsing

**Expected Barcode Count**

Parameter `ExpectedBarcodesCount` is an int value that refers to how many barcodes you would like to decode from a single image or frame. The barcode reader will try to find as many barcodes as the `ExpectedBarcodesCount` number. Set the `ExpectedBarcodesCount` to 1 can maximize the processing speed of your program but limit the read rate at the same time.

**Barcode Formats**

Parameter `BarcodeFormatIds` and `BarcodeFormatIds_2` are int values that controls the recognizable barcode formats. The fewer formats you set, the higher speed your app will be.

**Scale Down Threshold**

The image/frame will be continuously scaled down until it is smaller than the `ScaleDownThreshold`. You can use this parameter to improve the processing speed but the read rate and accuracy will decline on decoding the small-module barcode.

**Time out**

The parameter `Timeout` controls the maximum time consumption on processing a single image/frame. For image decoding scenarios, you can set a longer `Timeout` to ensure the barcode reader decode as many barcodes as possible from the image. For video barcode decoding scenarios, not all video frame contains a barcode. You can reduce the `Timeout` to enable your barcode reader to quickly quit the video frames without a barcode. The Timeout parameter benefits the speed of barcode decoding but might reduce the read rate.

**Deblur Modes**

The `DeblurModes` parameter enables the barcode reader to try different algorithms on processing the blurry barcodes. This parameter will benefit the read rate but reduce the processing speed.

### Other Settings

**Set Scan Region**

Configuring the scan region via `CameraEnhancer` method `setScanRegion` can further improve the barcode decoding speed. The video frames will be cropped based on the `scanRegion` setting before they are processed by the barcode reader. The `scanRegion` setting benefits the processing speed but might reduce the read rate at the same time.

<div align="center">
    <p><img src="assets/region-definition.png" width="70%" alt="region-def"></p>
    <p>Reduce the Size of Scan Area</p>
</div>

**Multi-Frame Verification**

When a barcode result has been decoded more than once within a short period of time, we can confirm it is a correct result and output it. However, if a barcode result has never been decoded a second time within a period of time, we consider it a misread result and discard it. You can enable the multi-frame verification to further improve the result accuracy via the method `enableResultVerification`.

**Frame Filter**

Frame filter is one of the camera enhancer features. You can enable it via `CameraEnhancer` method `enableFeatures`. The frame filter helps in filtering blurry video frames to improve the barcode decoding accuracy. It also improves the speed performance of low-end devices.

**Fast Mode**

Fast mode is one of the camera enhancer features. You can enable it via `CameraEnhancer` method `enableFeatures`. Similar to the `scanRegion` setting, the fast mode will crop the video frames into different sizes to improve the processing speed. You can configure the detailed cropping size via `CameraEnhancer` method `updateAdvanceSettings`. Please note, the method `setScanRegion` will negate the fast mode. Please select one of them when you want to implement the frame cropping.
