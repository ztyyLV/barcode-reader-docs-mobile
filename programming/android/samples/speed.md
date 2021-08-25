---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - Best Speed Settings Samples
description: This is the Best Speed Settings Samples page of Dynamsoft Barcode Reader for Android SDK.
keywords: android, samples, speed
needAutoGenerateSidebar: false
breadcrumbText: Best Speed
---

# Speed-first Settings

The Speed-first Settings sample illustrates how to improve the speed performance of the barcode decoding apps. Generally, users can improve the barcode decoding speed by reducing the size of the scan region or simplifying the complexity of the barcode settings. Further more, for certain scenarios, configuring parameter settings also contributes to the barcode reading speed. In this page, you will be guide on how to make personalized speed-friendly parameter settings for your barcode decoding app.

View the sample

- [Speed-first Settings Sample]()

## Size of the Scan Region

Reducing the scan region size is the most efficive way to speed up on the barcode reading. To reduce the scan region size, you can make settings on the border of the scan region via `PublicRuntimeSettings` and `RegionDefinition` class.

## The Barcode Setting

**The barcode count**

Normally, the barcode reader will try different parameter combinations to find as many barcodes as the expected number. If the expected barcode count is far more than the actual value, the barcode decoding speed will be decreased. As a result, to maximum the barcode decoding speed, please make sure to set the expected barcode count to an appropriate value.

**The barcode format**



## BarcodeFormat

The barcode reader will try all the preset barcode formats until it finds as many barcodes as the expected value. Supporting more barcode formats will definitely improve the read rate of your app on unknown usage scenarios. However, the reading speed will be sharply declined as well. If the supporting scope of your app is confirmed, please make sure to set the barcode format parameter exactly the same as your scope. This can save your computing resource to the greatest extent and help your app on improving its decoding speed.

## LocalizationModes

The Barcode Reader has several different barcode localization methods. Users can set the localization modes via the parameter `LocalizationModes`. The selection of localization mode can effectively improve the decoding speed.

## Templates

### For single barcode scanning

### For single barcode continuous scanning

### For general usage
