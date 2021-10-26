---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - Speed-first Settings Sample
description: This is the Speed-first Settings Sample page of Dynamsoft Barcode Reader for Android SDK.
keywords: android, sample, speed
needAutoGenerateSidebar: true
breadcrumbText: Speed-First Settings
---

# Speed-first Settings

The Speed-first Settings sample illustrates how to improve the speed performance of the barcode decoding apps. Generally, users can improve the barcode decoding speed by reducing the size of the scan region or simplifying the complexity of the barcode settings. Furthermore, for certain scenarios, configuring parameter settings also contributes to the barcode reading speed. On this page, you will be guided on how to make personalized speed-friendly parameter settings for your barcode decoding app.

View the sample

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/Performance/SpeedFirstSettings" target="_blank">Java (Android) Speed-first Settings Sample</a>

## Size of the Scan Region

Reducing the scan region size is the most effective way to speed up the barcode reading. To reduce the scan region size, you can restrict the border of the scan region via [`PublicRuntimeSettings`]({{ site.android_api }}auxiliary-PublicRuntimeSettings.html) and [`RegionDefinition`]({{ site.android_api }}auxiliary-RegionDefinition.html) classes. Displaying the scan region on the UI can also guide the users to manually approach the barcode area.

<div align="center">
    <p><img src="assets/region-definition.png" width="70%" alt="region-def"></p>
    <p>Reduce the Size of Scan Area</p>
</div>

## Simplify the Barcode Setting

**The barcode count**

Normally, the barcode reader will try different parameter combinations to find as many barcodes as the expected number. If the expected barcode count is far more than the actual value, the barcode decoding speed will be decreased. As a result, to maximum the barcode decoding speed, please make sure to set the expected barcode count to an appropriate value.

**The barcode format**

The barcode reader will switch between the preset barcode formats until it finds as many barcodes as the expected value. Supporting more barcode formats will benefit the coverage of your app but at the same time be negative on the reading speed. Please confirm that you have set the supporting barcode formats exactly the same as your expected usage scenario so that you can enable your app to reach the balance between speed and coverage.

## Parameter Control

Dynamsoft Barcode Reader provides APIs that enable users to make advanced mode & parameter settings. These modes and parameters can benefit the read rate of the barcode reader in different scenarios or maximum the speed and accuracy of a certain scenario.

**LocalizationModes**

The [`LocalizationModes`]({{ site.parameters_reference }}localization-modes.html) members are designed for different specified scenarios. On the aspect of barcode reading speed, **LM_ONED_FAST_SCAN** is the fastest mode for only one_D barcode scenarios and **LM_SCAN_DIRECTLY** is the best mode for multiple barcode formats scenarios. Please read more about the localization modes on the page of parameter [`LocalizationModes`]({{ site.parameters_reference }}localization-modes.html).

**BinarizationModes**

The fewer [`BinarizationModes`]({{ site.parameters_reference }}binarization-modes.html) are set, the faster the barcode reading speed will be. The default value of parameter [`EnableFillBinaryVacancy`]({{ site.parameters_reference }}binarization-modes.html#enablefillbinaryvacancy) is true, which means the vacant hollows will be filled by default. You can set [`EnableFillBinaryVacancy`]({{ site.parameters_reference }}binarization-modes.html#enablefillbinaryvacancy)
value false to improve the barcode reading speed but the read rate might be decreased at the same time.

For more information about **BinarizationModes**, please read the following article.

- [`BinarizationModes`]({{ site.scenario_settings }}how-to-set-binarization-modes.html)

**ScaleDownThreshold**

Parameter [`ScaleDownThreshold`]({{ site.parameters_reference }}scale-down-threshold.html) can improve the barcode reading speed by reducing the size of the scan area. When the [`ScaleDownThreshold`]({{ site.parameters_reference }}scale-down-threshold.html) value is configured, the barcode reader will try to shrink the input image continuously until the size of the image is smaller than the [`ScaleDownThreshold`]({{ site.parameters_reference }}scale-down-threshold.html) value.

**Timeout**

The parameter [`Timeout`]({{ site.parameters_reference }}time-out.html) can not directly reduce the processing time but enable the barcode reader to stop wasting time on decoding a single image. This parameter will be helpful on video barcode decoding or dealing with a large batch of barcodes.
