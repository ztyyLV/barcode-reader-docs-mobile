---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - iFrameDecodingParameters Class
description: This page shows the iFrameDecodingParameters Class of Dynamsoft Barcode Reader for iOS SDK.
keywords: iExtendedResult, class, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
---


# Class iFrameDecodingParameters

> Note:
>
> - This class is removed in 9.0 version. Please use the [video methods](primary-video.md) for video barcode scanning.

Defines a struct to configure the frame decoding Parameters.  

```objc
@interface iFrameDecodingParameters
```

| Attribute | Type | Descriptions |
|---------- | ---- | ------------ |
| [`maxQueueLength`](#maxqueuelength) | *NSInteger* | The maximum number of frames waiting for decoding. |
| [`maxResultQueueLength`](#maxresultqueuelength) | *NSInteger* | The maximum number of frames waiting results (text result/localization result) will be kept for further reference. |
| [`width`](#width) | *NSInteger* | The width of the frame image in pixels.  |
| [`height`](#height) | *NSInteger* | The height of the frame image in pixels. |
| [`stride`](#stride) | *NSInteger* | The stride (or scan width) of the frame image. |
| [`imagePixelFormat`](#imagepixelformat) | `EnumImagePixelFormat` | The image pixel format used in the image byte array. |
| [`region`](#region) | `iRegionDefinition` | The region definition of the frame to calculate the internal indicator. |
| [`threshold`](#threshold) | *float* | The threshold used for filtering frames. |
| [`fps`](#fps) | *NSInteger* | The frequency of calling `appendFrame` per second. |
| [`autoFilter`](#autofilter) | *NSInteger* | Sets whether to filter frames automatically. |
| [`clarityCalculationMethod`](#claritycalculationmethod) | `EnumClarityCalculationMethod` | Sets the method used for calculating the clarity of the frames. |
| [`clarityFilterMode`](#clarityfiltermode) | `EnumClarityFilterMode` | Sets the mode used for filtering frames by calculated clarity. |

## maxQueueLength

The maximum number of frames waiting for decoding.

```objc
NSInteger maxQueueLength
```

**Value Range**

[0,0x7fffffff]

**Default Value**

3

## maxResultQueueLength

The maximum number of frames waiting results (text result/localization result) will be kept for further reference.  

```objc
NSInteger maxResultQueueLength
```

**Value Range**

[0,0x7fffffff]

**Default Value**

10  

## width

The width of the frame image in pixels.

```objc
NSInteger width
```

**Value Range**

[0,0x7fffffff]

**Default Value**

0  

## height

The height of the frame image in pixels.

```objc
NSInteger height
```

**Value Range**

[0,0x7fffffff]

**Default Value**

0  

## stride

The stride (or scan width) of the frame image.

```objc
NSInteger stride
```

**Value Range**

[0,0x7fffffff]

**Default Value**

0

## imagePixelFormat

The image pixel format used in the image byte array.

```objc
EnumImagePixelFormat imagePixelFormat
```

**Value Range**

A value of `EnumImagePixelFormat` Enumeration items.

**Default Value**

`EnumImagePixelFormatGrayScaled`

**See Also**

`EnumImagePixelFormat`

## region

The region definition of the frame to calculate the internal indicator.

```objc
iRegionDefinition region
```

**Default Value**

`{ regionLeft = 0, regionRight = 100, regionTop = 0, regionBottom = 100, regionMeasuredByPercentage = 1 }`

**See Also**

`iRegionDefinition`

## threshold

The threshold used for filtering frames.

```objc
float threshold
```

**Value Range**

[0, 1]

**Default Value**

0.1

**Remarks**

The SDK will calculate an inner indicator for each frame from `AppendFrame`, if the change rate of the indicators between the current frame and the history frames is larger than the given threshold, the current frame will not be added to the inner frame queue waiting for decoding.

## fps

The frequency of calling `AppendFrame` per second.

```objc
NSInteger fps
```

**Value Range**

[0,0x7fffffff]

**Default Value**

0  

**Remarks**

0 means the frequency will be calculated automatically by the SDK.

## autoFilter

Sets whether to filter frames automatically.

```objc
NSInteger autoFilter
```

**Value Range**

[0,1]

**Default Value**

1  

**Remarks**

0: Diable filtering frames automatically. 1: Enable filtering frames automatically.

## clarityCalculationMethod

Sets the method used for calculating the clarity of the frames.

```objc
EnumClarityCalculationMethod clarityCalculationMethod
```

**Value Range**

Any one of the `EnumClarityCalculationMethod` Enumeration items.

**Default Value**

EnumClarityCalculationMethodContrast

**See Also**

`EnumClarityCalculationMethod`

## clarityFilterMode

Sets the mode used for filtering frames by calculated clarity.

```objc
EnumClarityFilterMode clarityFilterMode
```

**Value Range**

Any one of the `EnumClarityFilterMode` Enumeration items.

**Default Value**

EnumClarityFilterModeGeneral

**See Also**

`EnumClarityFilterMode`
