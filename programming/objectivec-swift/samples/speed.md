---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - Best Speed Settings Samples
description: This is the Best Speed Settings Samples page of Dynamsoft Barcode Reader for Android SDK.
keywords: android, samples, speed
needAutoGenerateSidebar: false
breadcrumbText: Best Speed
---

# Best Speed Settings

On this page, you can find useful guidelines on improving the decoding speed of the barcode reader.

The speed related parameters:

| Parameter Name | Description |
| -------------- | ----------- |
| [`ExpectedBarcodeCount`](#expectedbarcodecount) | The expected barcode count in the scan region. |
| [`BarcodeFormat`](#barcodeformat) | The barcode types in barcode format enumerations. |
| [`region`](#region) | The scan region. |
| [`BinarizationModes`](#binarizationmodes) | Configurations of the binarization mode parameters. |
| [`LocalizationModes`](#localizationmodes) | Configurations of the localization mode parameters. |

## ExpectedBarcodeCount

The barcode reader can't always recognize all the barcodes in the scan area at one time. To finally find as many barcodes as the expected count, the barcode reader will switch between different processing modes to reach the expected counts.

**Default Value**

0: The barcode count is unknown. The barcode reader will try to find at least 1 barcode.

**Recommended Value**

1: The barcode decoding process will reach the highest speed when the expected barcode count is 1. Make this setting when your app is specially designed for single barcode decoding.  
0: If the usage scenario of your app is unknown, you can set the barcode count 0.

## BarcodeFormat

The more complex the barcode format is, the slower the barcode reader will be. The barcode reader will try to recognize all the

## region

## BinarizationModes

## LocalizationModes

**Recommended Value**

`ONED_FAST_SCAN`: A new localization mode member that newly added in v8.8 edition. The `ONED_FAST_SCAN` is specially designed for speeding up 1D barcode localization.
