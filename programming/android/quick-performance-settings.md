---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - Optimize Performance
description: This is the Optimize Performance page of Dynamsoft Barcode Reader for Android SDK.
keywords: Guide, Android, Optimize Performance
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# Quick Setup -- Performance Settings

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

```java
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.deblurLevel = 9;

reader.updateRuntimeSettings(settings);
```

**Enlarge the resolution**

When decoding from the video streaming, it is recommended to set the resolution to 1080P.

```java
// You can use the following method to change the resolution.
cameraEnhancer.setResolution(EnumResolution.RESOLUTION_1080P);
```

## How to improve the Speed

### ScaleDownThreshold

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [512,0x7fffffff] | 2300 |

Images with larger sizes than the threshold will be scaled down. The default value of `ScaleDownThreshold` is 2300 (pixel). You can set a smaller value for the `ScaleDownThreshold` when you want to speed up the barcode decoding.

```java
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.scaleDownThreshold = 1200;
reader.updateRuntimeSettings(settings);
```

### Timeout

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,0x7fffffff] | 10000 |

`Timeout`, which is measured by milliseconds, determines the maximum time the barcode reader will spend on each single image. Setting a lower `Timeout` value might help you on improving the processing speed of video barcode decoding. Some low-end devices may not be able to complete the barcode processing if the `Timeout` is too short. Be sure to do enough tests to reserve enough time for low-end devices when configuring the `Timeout` setting.

```java
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.timeout = 9;
reader.updateRuntimeSettings(settings);
```

## Filter out the Misreading Results

### Confidence

| Value Type | Value Range | Default Value |
| ---------- | ----------- | ------------- |
| int | [0,100] | 30 |

`MinResultConfidence` is the parameter that controls the result confidence filter. The default value of `MinResultConfidence` is 30. You can set `MinResultConfidence` higher to get even more accurate results.

```java
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.minResultConfidence = 40;
reader.updateRuntimeSettings(settings);
```

### Result Verification

Use multiple barcode results from different video frames to verify the correctness of the results. You can enable the result verification to further improve the result accuracy.

## Other Settings

Through the above parameters, you can quickly adjust the performance of the barcode reader according to your usage scenario.
