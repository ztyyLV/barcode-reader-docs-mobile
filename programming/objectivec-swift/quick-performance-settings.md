---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - Optimize Performance
description: This is the Optimize Performance page of Dynamsoft Barcode Reader for iOS SDK.
keywords: Guide, Optimize Performance
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# Quickly Adjust on the Performance

By following the previous guide, I believe you have managed to create your own barcode reader project. However, you might be still stuck in some aspects:

- There are some barcodes I can't recognize.
- The processing speed is too slow.
- There are misreading results.

In this article, we will share some solutions to help you solve the above issues.

## How to Decode the Unrecognized Barcodes

There are several reasons that may cause a barcode unrecognized.

Generally speaking

- The barcode reader failed to locate the barcode.
- The barcode is located but the result cannot be decoded.

**Adjust the DeblurLevel**

`DeblurLevel` is the parameter that controls how much effort the library spends on decoding the localized barcodes. Set a higher value of the DeblurLevel will improve the recognition rate and decrease the recognition speed at the same time. `DeblurLevel` is set to 9 (the highest level) by default. Therefore, if you find the recognition speed is not satisfying, you can reduce the `DeblurLevel` to balance the performance.

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,9] | 9 |

```swift
let settings = try? barcodeReader.getRuntimeSettings()
settings.deblurLevel = 0
try? barcodeReader.updateRuntimeSettings(settings!)
```

**Enlarge the Resolution**

When decoding from the video streaming, it is recommended to set the resolution to 1080P.

```swift
dce.setResolution(Resolution.EnumRESOLUTION_1080P)
```

**Add Localization Modes**

The `LocalizationModes` determines how the library locates the barcode. Set multiple `LocalizationModes` can help the library to find at least one barcode for further processing. When you find there are barcodes that can't be recognized, you may try adding extra parameters to the `LocalizationModes`.

```swift
let settings = try? barcodeReader.getRuntimeSettings()
settings.localizationModes = [EnumLocalizationMode.scanDirectly, EnumLocalizationMode.connectedBlocks]
try? barcodeReader.updateRuntimeSettings(settings!)
```

## How to Improve the Speed

**Set ScaleDownThreshold**

Images with higher pixel density than the threshold will be scaled down. The default value of `ScaleDownThreshold` is 2300 (pixel). You can set a smaller value when you need to speed up the recognition.

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [512,0x7fffffff] | 2300 |

```swift
let settings = try? barcodeReader.getRuntimeSettings()
settings.scaleDownThreshold = 1200
try? barcodeReader.updateRuntimeSettings(settings!)
```

**Reduce Timeout for Video Streaming Barcode Decoding**

`Timeout`, which is measured by milliseconds, determines the maximum time the library will spend on each image. Decreasing the value of `Timeout` might help you on improving the recognition speed of video decoding. Some low-end devices may not be able to complete the barcode processing if the `Timeout` is too short. Ensure to fully test before given a suitable `Timeout` for low-end devices.

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,0x7fffffff] | 10000 |

```swift
let settings = try? barcodeReader.getRuntimeSettings()
settings.timeout = 500
try? barcodeReader.updateRuntimeSettings(settings!)
```

## How to Filter out the Misreading Results

**Increase Confidence Level**

`MinResultConfidence` is the parameter that controls the result confidence to filter the results below the set confidence. The default value of `MinResultConfidence` is 30. You can set `MinResultConfidence` higher to get even more accurate results.

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,100] | 30 |

```swift
let settings = try? barcodeReader.getRuntimeSettings()
settings.minResultConfidence = 50
try? barcodeReader.updateRuntimeSettings(settings!)
```

**Enable Result Verification**

Use multiple barcode results from different video frames to verify the correctness of the results. You can enable the result verification to further improve the result accuracy.

```swift
reader.enableResultVerification = true
```

## Other Settings

If the above settings can not solve the issues you have, feel free to <a href="https://www.dynamsoft.com/company/contact/" target="_blank">contact us</a> for further technical support. DBR has a lot of built-in parameters for image processing, localization supporting and barcode decoding. Please feedback your problems to us so that our technical support team will help you configure the parameters to match your requirements.
