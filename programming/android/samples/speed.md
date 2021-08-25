---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - Best Speed Settings Samples
description: This is the Best Speed Settings Samples page of Dynamsoft Barcode Reader for Android SDK.
keywords: android, samples, speed
needAutoGenerateSidebar: false
breadcrumbText: Best Speed
---

# Speed-first Settings

The Speed-first Settings sample illustrates how to improve the speed performance of the barcode decoding apps. Generally, users can improve the barcode decoding speed by reducing the size of the scan region or simplifying the complexity of the barcode settings. Furthermore, for certain scenarios, configuring parameter settings also contributes to the barcode reading speed. On this page, you will be guided on how to make personalized speed-friendly parameter settings for your barcode decoding app.

View the sample

- [Speed-first Settings Sample]()

## Size of the Scan Region

Reducing the scan region size is the most effective way to speed up the barcode reading. To reduce the scan region size, you can restrict the border of the scan region via `PublicRuntimeSettings` and `RegionDefinition` classes. Displaying the scan region on the UI can also guide the users to manually approach the barcode area.

<div align="center">
    <p><img src="assets/region-definition.png" width="70%" alt="region-def"></p>
    <p>Reduce the Size of Scan Area</p>
</div>

## Simplify the Barcode Setting

**The barcode count**

Normally, the barcode reader will try different parameter combinations to find as many barcodes as the expected number. If the expected barcode count is far more than the actual value, the barcode decoding speed will be decreased. As a result, to maximum the barcode decoding speed, please make sure to set the expected barcode count to an appropriate value.

**The barcode format**

The barcode reader will switch between the preset barcode formats until it finds as many barcodes as the expected value. Supporting more barcode formats will benefit the coverage of your app but at the same time be negative on the reading speed. Please confirm that you have set the supporting barcode formats exactly the same as your expected usage scenario. So that you can enable your app to reach the balance between speed and coverage.

## Parameter Control

**LocalizationModes**

**BinarizationModes**

**ColourConversionModes**

## Templates

**For single barcode scanning**

**For general usage**
