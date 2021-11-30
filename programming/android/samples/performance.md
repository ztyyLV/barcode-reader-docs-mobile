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

## Single Barcode Performance

- `VIDEO_SINGLE_BARCODE`

## Speed First Performance

**Template**

- `VIDEO_SPEED_FIRST`
- `IMAGE_SPEED_FIRST`

**Set Scan Region**

Reducing the scan region size is the most effective way to speed up the barcode reading. To reduce the scan region size, you can restrict the border of the scan region via [`PublicRuntimeSettings`]({{ site.android_api }}auxiliary-PublicRuntimeSettings.html) and [`RegionDefinition`]({{ site.android_api }}auxiliary-RegionDefinition.html) classes. Displaying the scan region on the UI can also guide the users to manually approach the barcode area.

<div align="center">
    <p><img src="assets/region-definition.png" width="70%" alt="region-def"></p>
    <p>Reduce the Size of Scan Area</p>
</div>

## Read-Rate First Performance

- `VIDEO_READ_RATE_FIRST`
- `IMAGE_READ_RATE_FIRST`

## Accuracy First Performance

$ Speed = \frac{Total~Time~Consumption}{All~decoded~Barcode~Results} $

$ ReadRate = \frac{All~Decoded~Barcode~Results}{All~Existing~Barcodes} $

$ Accuracy = \frac{Correct~Barcode~Results}{All~decoded~Barcode~Results} $

There is no template for accuracy settings. The default template is accurate enough for general usage. To further improve the accuracy for your usage scenarios, you can add the following configuration to your program.

**Multi-Frame Confirmation**

A large number of barcode results can be decoded from multiple video frames when using video barcode decoding. In this usage scenario, the correctness of each barcode result can be confirmed when a same barcode text is decoded  the neighbouring video frames.

**Error-Prone Barcode Filter**

**Result Filter**

**Disable Deblur**

**Camera Enhancer Settings**
