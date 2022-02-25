---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - Advanced Usage
description: This is the Advanced Usage page of Dynamsoft Barcode Reader for iOS SDK.
keywords: Guide, iOS, Settings
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# Improve Performance

If you have completed the page of basic settings, you might have a basic understanding on how to use PublicRuntimeSettings to configure the barcode settings

## DeblurLevel

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,9] | 9 |

`DeblurLevel` is the parameter that controls how much effort the barcode reader spends on decoding the localized barcodes. Setting the DeblurLevel higher will improve the barcode decoding read rate but decline the processing speed at the same time. `DeblurLevel` is set to 9 (the highest level) by default. Therefore, if you find the processing speed is not satisfying, you can reduce the `DeblurLevel` to balance the speed and read rate performance.

**Recommendations**

| Image Source | Priority | DeblurLevel |
| ------------ | -------- | ----------- |
| Static Image | Speed | 0-6 |
| Static Image | Read Rate | 7-9 |
| Video streaming | Speed | 0-3 |
| Video streaming | Read Rate | 4-9 |

## Timeout

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,0x7fffffff] | 10000 |

`Timeout`, which is measured by milliseconds, determines the maximum time the barcode reader will spend on each single image. Set a lower `Timeout` value might help you on improving the processing speed of video barcode decoding. Some low end device may not be able to complete the barcode processing if the `Timeout` is too short. Be sure to do enough test to reserve enough time for low end devices when configuring the `Timeout` setting.

## Confidence

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,100] | 30 |

`MinResultConfidence` is the parameter that controls the result confidence filter. The default value of `MinResultConfidence` is 30. You can set `MinResultConfidence` higher to get even more accurate results.

## Result Verification

Use multiple barcode results from different video frames to verify the correctness of the results. You can enable the result verification to further improve the result accuracy.

## ScaleDownThreshold

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [512,0x7fffffff] | 2300 |

Images with larger size then the threshold will be scaled down. The default value of `ScaleDownThreshold` is 2300 (pixel). You can set a smaller value for the `ScaleDownThreshold` when you want to speed up the barcode decoding.
