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

Since you have created a simple barcode reader and added barcode format settings.

## DeblurLevel

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,9] | 9 |

`DeblurLevel` is the parameter that controls how much effort the barcode reader spends on decoding the localized barcodes. Generally, the higher `DeblurLevel` leads to higher ability on decoding blurry barcode.

**Recommendations**

- For image decoding: 9
- Video streaming barcode decoding: 0-5
- Video streaming barcode

| Image Source | Pirority | DeblurLevel |
| ------------ | -------- | ----------- |
| Static Image | Speed | 0-6 |
| Static Image | Read Rate | 7-9 |
| Video streaming | Speed | 0 |
| Video streaming | Read Rate | 1-9 |

## Timeout

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,0x7fffffff] | 10000 |

The parameter timeout determines the maximum time that the barcode reader spends on processing each image. It is recommended to set a higher timeout value for image decoding and a lower timeout for video streaming barcode decoding.

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
