---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - Read-Rate-First Settings Samples
description: This is the Read-Rate-First Settings Sample page of Dynamsoft Barcode Reader for Android SDK.
keywords: android, samples, speed
needAutoGenerateSidebar: false
breadcrumbText: Read-Rate-First Settings
---

# Android ReadRateFirstSettings Sample

The Read-Rate-First Settings Sample illustrates how to maximize the rate when using Dynamsoft Barcode Reader Android SDK. Generally, the Read Rate of a barcode reader refers to the rate of successfully recognized barcode among all barcodes in the given image in one scan.

**View Samples (on GitHub)**

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/Performance" target="_blank">Read-Rate-First Settings Sample (Android Java)</a>

## Regular Settings

### The Scan Region

It is not recommened to make configurations on the scan region if the app is focusing on improving the Read-Rate. Dynamsoft Barcode Reader Android SDK will scan the full image by default.

### The Format Specification

The barcode formats can be specified via `PublicRuntimeSetting`. The default value of DBR is not supporting all available barcode formats. Optimize the barcode format settings to cover the requirements will help you to create a high-efficiency and high-read-rate barcode reader that covers your usage scenario.

**Related APIs**

- View class [`PublicRuntimeSetting`]({{ site.android_api }}auxiliary-PublicRuntimeSettings.html) to learn about the default barcode formats.
- View Enum [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) and [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2) to learn about all available barcode formats.

### The Barcode Count

The barcode count setting determines the maximum barcodes the barcode reader can recognize at once from a single image/frame. Increasing the expected barcode count benefits the read rate but declines the reading speed at the same time.

## Modes Parameter Settings

Suppose the barcode format and the barcode count are completely set. The main factors that determine the read rate are how to localize as many barcodes as possible and how to recognize all the localized barcodes.

### Localization Friendly Parameters

The following pre-processing modes parameter settings will benefit the localization process. The barcode reader always tries different parameter combinations to find as many barcodes as the pre-set value. Despite the influence on processing speed, pre-set more parameters will definitely improve the read rate of your barcode reader.

| Modes Parameter | Description |
| --------------- | ----------- |
| [`ColourConversionModes`] | Convert the coloured image into grayscale image. |
| [`GrayscaleTransformationModes`] | Switch between the original and invert image when processing the grayscale images. |
| [`RegionPredetectionModes`] | Algorithm that pre-detect the barcode region. |
| [`ImagePreprocessingModes`] | Pre-processing on the barcodes for different scenarios. |
| [`BinarizationModes`] | Pre-processing on the barcodes by binarization. |
| [`LocalizationModes`] | The modes that applied to localize the barcode. |

### Barcode Reading Friendly Parameters

The following parameters will benefit the barcode decoding.

| Modes Parameter | Description |
| --------------- | ----------- |
| [`ScaleUpModes`] | Enhance the read rate of small sized barcodes. |
| [`DeformationResistingModes`] | Enhance the read rate of deformed barcodes (QR & DataMatrix barcodes only). |
| [`DeblurModes`] | Enhance the read rate when processing a blurry image. |
| [`MirrorMode`] | Try decoding by mirroring the barcodes. |
| [`DPMCodeReadingModes`] | Enhance the recognition of DPM barcodes. |
