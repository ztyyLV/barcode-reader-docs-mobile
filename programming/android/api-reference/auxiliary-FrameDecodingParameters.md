---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - FrameDecodingParameters Class
description: This page shows the FrameDecodingParameters Class of Dynamsoft Barcode Reader for Android SDK.
keywords: FrameDecodingParameters, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---


# Class FrameDecodingParameters

Defines a struct to configure the frame decoding Parameters.  

| Attribute | Type |
|---------- | ---- |
| [`maxQueueLength`](#maxqueuelength) | *int* |
| [`maxResultQueueLength`](#maxresultqueuelength) | *int* |
| [`width`](#width) | *int* |
| [`height`](#height) | *int* |
| [`stride`](#stride) | *int* |
| [`imagePixelFormat`](#imagepixelformat) | *int* |
| [`region`](#region) | [`RegionDefinition`](auxiliary-RegionDefinition.md) |
| [`threshold`](#threshold) | *float* |
| [`fps`](#fps) | *int* |
| [`autoFilter`](#autofilter) | *int* |
| [`clarityCalculationMethod`](#claritycalculationmethod) | *int* |
| [`clarityFilterMode`](#clarityfiltermode) | *int* |

## maxQueueLength

The maximum number of frames waiting for decoding.

```java
int maxQueueLength
```

- **Value range**
    [0,0x7fffffff]

- **Default value**
    3

## maxResultQueueLength

The maximum number of frames waiting results (text result/localization result) will be kept for further reference.  

```java
int maxResultQueueLength
```

- **Value range**
    [0,0x7fffffff]

- **Default value**
    10  

## width

The width of the frame image in pixels.

```java
int width
```

- **Value range**
    [0,0x7fffffff]

- **Default value**
    0  

## height

The height of the frame image in pixels.

```java
int height
```

- **Value range**
    [0,0x7fffffff]

- **Default value**
    0  

## stride

The stride (or scan width) of the frame image.

```java
int stride
```

- **Value range**
    [0,0x7fffffff]

- **Default value**
    0

## imagePixelFormat

The image pixel format used in the image byte array.

```java
int imagePixelFormat
```

- **Value range**
    A value of [`EnumImagePixelFormat`]({{ site.enumerations }}other-enums.html#imagepixelformat) Enumeration items.

- **Default value**
    `IPF_GRAYSCALED`

- **See also**  
    [`EnumImagePixelFormat`]({{ site.enumerations }}other-enums.html#imagepixelformat)

## region

The region definition of the frame to calculate the internal indicator.  

```java
RegionDefinition region
```

- **Default value**  
    `{ regionLeft = 0, regionRight = 100, regionTop = 0, regionBottom = 100, regionMeasuredByPercentage = 1 }`

- **See also**
    [`RegionDefinition`](RegionDefinition.md)

## threshold

The threshold used for filtering frames.

```java
float threshold
```

- **Value range**
    [0, 1]

- **Default value**
    0.1

- **Remarks**  
    The SDK will calculate an inner indicator for each frame from [`appendFrame`](../BarcodeReader/video.md#appendframe), if the change rate of the indicators between the current frame and the history frames is larger than the given threshold, the current frame will not be added to the inner frame queue waiting for decoding.

## fps

The frequency of calling [`appendFrame`](../BarcodeReader/video.md#appendframe) per second.

```java
int fps
```

- **Value range**
    [0,0x7fffffff]

- **Default value**
    0  

- **Remarks**  
    0 means the frequency will be calculated automatically by the SDK.

## autoFilter

Sets whether to filter frames automatically.

```java
int autoFilter
```

- **Value range**
    [0,1]

- **Default value**
    1  

- **Remarks**  
    0: Diable filtering frames automatically. 1: Enable filtering frames automatically.

## clarityCalculationMethod

Sets the method used for calculating the clarity of the frames.

```java
int clarityCalculationMethod
```

- **Value range**
    Any one of the [`EnumClarityCalculationMethod`]({{ site.enumerations }}frame-decoding-enums.html#claritycalculationmethod) Enumeration items.

- **Default value**
    ECCM_CONTRAST

- **See also**  
    [`EnumClarityCalculationMethod`]({{ site.enumerations }}frame-decoding-enums.html#claritycalculationmethod)

## clarityFilterMode

Sets the mode used for filtering frames by calculated clarity.

```java
int clarityFilterMode
```

- **Value range**
    Any one of the [`EnumClarityFilterMode`]({{ site.enumerations }}frame-decoding-enums.html#clarityfiltermode) Enumeration items.

- **Default value**
    CFM_GENERAL

- **See also**  
    [`EnumClarityFilterMode`]({{ site.enumerations }}frame-decoding-enums.html#clarityfiltermode)
