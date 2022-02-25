---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - Optimize Performance
description: This is the Optimize Performance page of Dynamsoft Barcode Reader for Android SDK.
keywords: Guide, Android, Optimize Performance
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# Quickly Adjust on the Performance

If you have followed the previous steps, you got a basic video streaming barcode reading app. However, you might be still puzzled by the following issues:

- There are some barcodes I can't recognize.
- The processing speed is too slow.
- There are misreading results.

Some simple solutions are given on this page. They may help you quickly solve the above issues.

## How to Decode the Unreadable Barcodes

There are multiple reasons that may cause a barcode is not recognized. Generally, the reason can be summarized as follow:

- The barcode is localized but the barcode reader can't get the barcode result from the localized area.
- The barcode reader failed to localize the barcode.

**Increase the DeblurLevel**

`DeblurLevel` is the parameter that controls how much effort the barcode reader spends on decoding the localized barcodes. Setting the DeblurLevel higher will improve the barcode decoding read rate but decline the processing speed at the same time. `DeblurLevel` is set to 9 (the highest level) by default. Therefore, if you find the processing speed is not satisfying, you can reduce the `DeblurLevel` to balance the speed and read rate performance.

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,9] | 9 |

```swift
let settings = try! barcodeReader.getRuntimeSettings()
settings.deblurLevel = 0
barcodeReader.update(settings, error: &error)
```

**Enlarge the resolution**

When decoding from the video streaming, it is recommended to set the resolution to 1080P.

```swift
dce.setResolution(Resolution.EnumRESOLUTION_1080P)
```

**Add Localization Modes**

The `LocalizationModes` determines how the barcode reader localizes the barcodes. The barcode reader will switch the `LocalizationModes` to find at least one barcode for further processing. When you find there are several barcodes can't be recognized, you may try adding more modes to the `LocalizationModes` configuration.

```swift
let settings = try! barcodeReader.getRuntimeSettings()
settings.localizationModes = [EnumLocalizationMode.scanDirectly, EnumLocalizationMode.connectedBlocks]
barcodeReader.update(settings, error: &error)
```

## How to Improve the Speed

**Set ScaleDownThreshold**

Images with larger sizes than the threshold will be scaled down. The default value of `ScaleDownThreshold` is 2300 (pixel). You can set a smaller value for the `ScaleDownThreshold` when you want to speed up the barcode decoding.

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [512,0x7fffffff] | 2300 |

```swift
let settings = try! barcodeReader.getRuntimeSettings()
settings.scaleDownThreshold = 1200
barcodeReader.update(settings, error: &error)
```

**Reduce Timeout for Video Streaming Barcode Decoding**

`Timeout`, which is measured by milliseconds, determines the maximum time the barcode reader will spend on each single image. Setting a lower `Timeout` value might help you on improving the processing speed of video barcode decoding. Some low-end devices may not be able to complete the barcode processing if the `Timeout` is too short. Be sure to do enough tests to reserve enough time for low-end devices when configuring the `Timeout` setting.

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,0x7fffffff] | 10000 |

```swift
let settings = try! barcodeReader.getRuntimeSettings()
settings.timeout = 500
barcodeReader.update(settings, error: &error)
```

## How to Filter out the Misreading Results

**Increase Confidence Level**

`MinResultConfidence` is the parameter that controls the result confidence filter. The default value of `MinResultConfidence` is 30. You can set `MinResultConfidence` higher to get even more accurate results.

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,100] | 30 |

```swift
let settings = try! barcodeReader.getRuntimeSettings()
settings.minResultConfidence = 50
barcodeReader.update(settings, error: &error)
```

**Enable Result Verification**

Use multiple barcode results from different video frames to verify the correctness of the results. You can enable the result verification to further improve the result accuracy.

```swift
reader.enableResultVerification = true
```

## Other Settings

If the above settings can not solve the issues you met, feel free to <a href="https://www.dynamsoft.com/company/contact/" target="_blank">contact us</a> for further technical support. DBR has a lot of built-in parameters for image processing, localization supporting and barcode decoding. Please feedback your problems to us so that our technical support team will help you configure the parameters to match your requirements.
