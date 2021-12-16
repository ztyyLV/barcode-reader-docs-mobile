---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - Performance Settings Sample
description: This is the Performance Settings Sample page of Dynamsoft Barcode Reader for iOS SDK.
keywords: iOS, sample, Performance
needAutoGenerateSidebar: true
breadcrumbText: Performance Settings
---

# PerformanceSettings Sample

View the sample

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Objective-C/PerformanceSettingsObjC" target="_blank">Objective-C Performance Settings Sample</a>
- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Swift/PerformanceSettingsSwift" target="_blank">Swift Performance Settings Sample</a>

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

Parameter [`ExpectedBarcodesCount`]({{site.parameters_reference}}expected-barcodes-count.html) is an int value that refers to how many barcodes you would like to decode from a single image or frame. The barcode reader will try to find as many barcodes as the [`ExpectedBarcodesCount`]({{site.parameters_reference}}expected-barcodes-count.html) number. Set the [`ExpectedBarcodesCount`]({{site.parameters_reference}}expected-barcodes-count.html) to 1 can maximize the processing speed of your program but limit the read rate at the same time.

**Barcode Formats**

Parameter [`BarcodeFormatIds`]({{site.parameters_reference}}barcode-format-ids.html) and [`BarcodeFormatIds_2`](({{site.parameters_reference}}barcode-format-ids-2.html)) are int values that controls the recognizable barcode formats. The fewer formats you set, the higher speed your app will be.

**Scale Down Threshold**

The image/frame will be continuously scaled down until it is smaller than the [`ScaleDownThreshold`]({{site.parameters_reference}}scale-down-threshold.html). You can use this parameter to improve the processing speed but the read rate and accuracy will decline on decoding the small-module barcode.

**Time out**

The parameter [`Timeout`]({{site.parameters_reference}}time-out.html) controls the maximum time consumption on processing a single image/frame. For image decoding scenarios, you can set a longer [`Timeout`]({{site.parameters_reference}}time-out.html) to ensure the barcode reader decode as many barcodes as possible from the image. For video barcode decoding scenarios, not all video frame contains a barcode. You can reduce the [`Timeout`]({{site.parameters_reference}}time-out.html) to enable your barcode reader to quickly quit the video frames without a barcode. The Timeout parameter benefits the speed of barcode decoding but might reduce the read rate.

**Deblur Modes**

The [`DeblurModes`]({{site.parameters_reference}}deblur-modes.html) parameter enables the barcode reader to try different algorithms on processing the blurry barcodes. This parameter will benefit the read rate but reduce the processing speed.

### Other Settings

**Set Scan Region**

Configuring the scan region via **CameraEnhancer** method <a href="https://www.dynamsoft.com/camera-enhancer/docs/programming/ios/primary-api/camera-enhancer.html?ver=latest#setscanregion" target="_blank">`setScanRegion`</a> can further improve the barcode decoding speed. The video frames will be cropped based on the **scanRegion** setting before they are processed by the barcode reader. The **scanRegion** setting benefits the processing speed but might reduce the read rate at the same time.

<div align="center">
    <p><img src="assets/region-definition.png" width="70%" alt="region-def"></p>
    <p>Reduce the Size of Scan Area</p>
</div>

**Multi-Frame Verification**

When a barcode result has been decoded more than once within a short period of time, we can confirm it is a correct result and output it. However, if a barcode result has never been decoded a second time within a period of time, we consider it a misread result and discard it. You can enable the multi-frame verification to further improve the result accuracy via the method [`enableResultVerification`]({{site.oc_api}}primary-result.html#enableresultverification).

**Frame Filter**

Frame filter is one of the camera enhancer features. You can enable it via **CameraEnhancer** method <a href="https://www.dynamsoft.com/camera-enhancer/docs/programming/ios/primary-api/camera-enhancer.html?ver=latest#enablefeatures" target="_blank">`enableFeatures`</a>. The frame filter helps in filtering blurry video frames to improve the barcode decoding accuracy. It also improves the speed performance of low-end devices.

**Fast Mode**

Fast mode is one of the camera enhancer features. You can enable it via **CameraEnhancer** method <a href="https://www.dynamsoft.com/camera-enhancer/docs/programming/ios/primary-api/camera-enhancer.html?ver=latest#enablefeatures" target="_blank">`enableFeatures`</a>. Similar to the **scanRegion** setting, the fast mode will crop the video frames into different sizes to improve the processing speed. You can configure the detailed cropping size via **CameraEnhancer** method <a href="https://www.dynamsoft.com/camera-enhancer/docs/programming/ios/primary-api/camera-enhancer.html?ver=latest#updateadvancedsettingsfromfile" target="_blank">`updateAdvanceSettings`</a>. Please note, the method <a href="https://www.dynamsoft.com/camera-enhancer/docs/programming/ios/primary-api/camera-enhancer.html?ver=latest#setscanregion" target="_blank">`setScanRegion`</a> will negate the fast mode. Please select one of them when you want to implement the frame cropping.
