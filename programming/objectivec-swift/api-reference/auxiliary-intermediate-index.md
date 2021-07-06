---
layout: default-layout
title: Dynamsoft Barcode Reader iOS API Reference - iIntermediateResult index
description: This page shows the iIntermediateResult index of Dynamsoft Barcode Reader for iOS SDK.
keywords: IntermediateResult, api reference, iOS
needAutoGenerateSidebar: true
needGenerateH3Content: False
---

# Intermediate Result Classes

## Class iIntermediateResult

```objc
@interface iIntermediateResult 
```  

| Attribute | Type | Description |
|---------- | ---- | ----------- |
| [`resultsCount`](#resultscount) | *NSInteger* | The total result count. |
| [`results`](#results) | *NSObject\** | One of the following types: Array of [`Contour`](auxiliary-contour.md), Array of [`ImageData`](auxiliary-imagedata.md), Array of [`LineSegment`](auxiliary-linesegment.md), Array of [`LocalizationResult`](auxiliary-localizationresult.md), Array of [`RegionOfInterest`](auxiliary-regionofinterest.md). |
| [`dataType`](#datatype) | [`EnumIMResultDataType`]({{ site.enumerations }}result-enums.html#imresultdatatype) | The data type of the intermediate result. |
| [`resultType`](#resulttype) | [`EnumIntermediateResultType`]({{ site.enumerations }}result-enums.html#intermediateresulttype) | Intermediate result type. |
| [`barcodeComplementMode`](#barcodecomplementmode) | [`EnumBarcodeComplementMode`]({{ site.enumerations }}parameter-mode-enums.html#barcodecomplementmode) | The [`EnumBarcodeComplementMode`]({{ site.enumerations }}parameter-mode-enums.html#barcodecomplementmode) used when generating the current intermediate result. |
| [`bcmIndex`](#bcmindex) | *NSInteger* | The array index of current used [`EnumBarcodeComplementMode`]({{ site.enumerations }}parameter-mode-enums.html#barcodecomplementmode) in the [`barcodeComplementModes`](auxiliary-FurtherModes.md#barcodecomplementmodes) setting. |
| [`deformationResistingMode`](#deformationresistingmode) | [`EnumDeformationResistingMode`]({{ site.enumerations }}parameter-mode-enums.html#deformationresistingmode) | The [`EnumDeformationResistingMode`]({{ site.enumerations }}parameter-mode-enums.html#deformationresistingmode) used when generating the current intermediate result. |
| [`drmIndex`](#drmindex) | *NSInteger* | The array index of current used [`EnumDeformationResistingMode`]({{ site.enumerations }}parameter-mode-enums.html#deformationresistingmode) in the [`deformationResistingModes`](auxiliary-FurtherModes.md#deformationresistingmodes) setting. |
| [`dpmCodeReadingMode`](#dpmcodereadingmode) | [`EnumDPMCodeReadingMode`]({{ site.enumerations }}parameter-mode-enums.html#dpmcodereadingmode) | The [`EnumDPMCodeReadingMode`]({{ site.enumerations }}parameter-mode-enums.html#dpmcodereadingmode) used when generating the current intermediate result. |
| [`dpmcrmIndex`](#dpmcrmindex) | *NSInteger* | The array index of current used [`EnumDPMCodeReadingMode`]({{ site.enumerations }}parameter-mode-enums.html#dpmcodereadingmode) in the [`dpmCodeReadingModes`](auxiliary-FurtherModes.md#dpmcodereadingmodes) setting. |
| [`transformationMatrix`](#transformationMatrix) | *NSArray \** | The rotation matrix. |
| [`textFilterMode`](#textfiltermode) | [`EnumTextFilterMode`]({{ site.enumerations }}parameter-mode-enums.html#textfiltermode) | The [`EnumTextFilterMode`]({{ site.enumerations }}parameter-mode-enums.html#textfiltermode) used when generating the current intermediate result. |
| [`tfmIndex`](#tfmindex) | *NSInteger* | The array index of current used [`EnumTextFilterMode`]({{ site.enumerations }}parameter-mode-enums.html#textfiltermode) in the [`textFilterModes`](auxiliary-FurtherModes.md#textfiltermodes) setting. |
| [`localizationMode`](#localizationmode) | [`EnumLocalizationMode`]({{ site.enumerations }}parameter-mode-enums.html#localizationmode) | The [`EnumLocalizationMode`]({{ site.enumerations }}parameter-mode-enums.html#localizationmode) used when generating the current intermediate result. |
| [`lmIndex`](#lmindex) | *NSInteger* | The array index of current used [`EnumLocalizationMode`]({{ site.enumerations }}parameter-mode-enums.html#localizationmode) in the [`localizationModes`](auxiliary-PublicRuntimeSettings.md#localizationmodes) setting. |
| [`binarizationMode`](#binarizationmode) | [`EnumBinarizationMode`]({{ site.enumerations }}parameter-mode-enums.html#binarizationmode) | The [`EnumBinarizationMode`]({{ site.enumerations }}parameter-mode-enums.html#binarizationmode) used when generating the current intermediate result. |
| [`bmIndex`](#bmindex) | *NSInteger* | The array index of current used [`EnumBinarizationMode`]({{ site.enumerations }}parameter-mode-enums.html#binarizationmode) in the [`binarizationModes`](auxiliary-PublicRuntimeSettings.md#binarizationmodes) setting. |
| [`imagePreprocessingMode`](#imagepreprocessingmode) | [`EnumImagePreprocessingMode`]({{ site.enumerations }}parameter-mode-enums.html#imagepreprocessingmode) | The [`EnumImagePreprocessingMode`]({{ site.enumerations }}parameter-mode-enums.html#imagepreprocessingmode) used when generating the current intermediate result. |
| [`ipmIndex`](#ipmindex) | *NSInteger* | The array index of current used [`EnumImagePreprocessingMode`]({{ site.enumerations }}parameter-mode-enums.html#imagepreprocessingmode) in [`imagePreprocessingModes`](auxiliary-FurtherModes.md#imagepreprocessingmodes) setting. |
| [`roiId`](#roiid) | *NSInteger* | The ID of the ROI (Region Of Interest) generated by the SDK. -1 means the original image. |
| [`regionPredetectionMode`](#regionpredetectionmode) | [`EnumRegionPredetectionMode`]({{ site.enumerations }}parameter-mode-enums.html#regionpredetectionmode) | The [`EnumRegionPredetectionMode`]({{ site.enumerations }}parameter-mode-enums.html#regionpredetectionmode) used when generating the current intermediate result. |
| [`rpmIndex`](#rpmindex) | *NSInteger* | The array index of current used [`EnumRegionPredetectionMode`]({{ site.enumerations }}parameter-mode-enums.html#regionpredetectionmode) in the [`regionPredetectionModes`](auxiliary-FurtherModes.md#regionpredetectionmodes) setting. |
| [`grayscaleTransformationMode`](#grayscaletransformationmode) | [`EnumGrayscaleTransformationMode`]({{ site.enumerations }}parameter-mode-enums.html#grayscaletransformationmode) | The [`EnumGrayscaleTransformationMode`]({{ site.enumerations }}parameter-mode-enums.html#grayscaletransformationmode) used when generating the current intermediate result. |
| [`gtmIndex`](#gtmindex) | *NSInteger* | The array index of current used [`EnumGrayscaleTransformationMode`]({{ site.enumerations }}parameter-mode-enums.html#grayscaletransformationmode) in the [`grayscaleTransformationModes`](auxiliary-FurtherModes.md#grayscaletransformationmodes) setting. |
| [`colourConversionMode`](#colourconversionmode) | [`EnumColourConversionMode`]({{ site.enumerations }}parameter-mode-enums.html#colourconversionmode) | The [`EnumColourConversionMode`]({{ site.enumerations }}parameter-mode-enums.html#colourconversionmode) used when generating the current intermediate result. |
| [`cicmIndex`](#cicmindex) | *NSInteger* | The array index of current used [`EnumColourConversionMode`]({{ site.enumerations }}parameter-mode-enums.html#colourconversionmode) in the [`colourConversionModes`](auxiliary-FurtherModes.md#colourconversionmodes) setting. |
| [`colourClusteringMode`](#colourclusteringmode) | [`EnumColourClusteringMode`]({{ site.enumerations }}parameter-mode-enums.html#colourclusteringmode) | The [`EnumColourClusteringMode`]({{ site.enumerations }}parameter-mode-enums.html#colourclusteringmode) used when generating the current intermediate result. |
| [`ccmIndex`](#ccmindex) | *NSInteger* | The array index of current used [`EnumColourClusteringMode`]({{ site.enumerations }}parameter-mode-enums.html#colourclusteringmode) in the [`colourClusteringModes`](auxiliary-FurtherModes.md#colourclusteringmodes) setting. |
| [`scaleDownRatio`](#scaledownratio) | *NSInteger* | The scale down ratio. |
| [`frameId`](#frameid) | *NSInteger* | The ID of the operated frame. |

## [iContour](auxiliary-contour.md)

```objc
@interface iContour
```  

`contour` is one of the [`results`](#intermediateresult) type in `IntermediateResult`.

| Attribute | Type | Description |
|---------- | ---- | ----------- |
| [`pointsCount`](#pointscount) |  *NSInteger* | The total points count of the contour. |
| [`points`](#points) | [NSArray*](auxiliary-iDBRPoint.md) \* | The points array of the points that surround the barcode area.. |

## [iImageData](auxiliary-imagedata.md)

```objc
@interface iImageData
```

`ImageData` is one of the [`results`](#intermediateresult) type in `IntermediateResult`.

| Attribute | Type | Description |
|---------- | ---- | ----------- |
| [`bytes`](#bytes) | *unsigned char\** | The image data content in a byte array. |
| [`bytesLength`](#byteslength) | *NSInteger* | The length of the image data byte array. |
| [`width`](#width) | *NSInteger* | The width of the image in pixels. |
| [`height`](#height) | *NSInteger* | The height of the image in pixels. |
| [`stride`](#stride) | *NSInteger* | The stride (or scan width) of the image. |
| [`format`](#format) | [`EnumImagePixelFormat`]({{ site.enumerations }}other-enums.html#imagepixelformat) | The image pixel format used in the image byte array. |

## [iLineSegment](auxiliary-linesegment.md)

```objc
@interface iLineSegment
```  

`LineSegment` is one of the [`results`](auxiliary-intermediateresult.md#results) type in `IntermediateResult`.

| Attribute | Type | Description |
|---------- | ---- | ----------- |
| [`startPoint`](#startpoint) | [`CGPoint`](auxiliary-iDBRPoint.md) | The start point of the line segment. |
| [`endPoint`](#endpoint) | [`CGPoint`](auxiliary-iDBRPoint.md) | The end point of the line segment. |
| [`linesConfidenceCoefficients`](#linesconfidencecoefficients) | *NSData \** | *byte\[\]* | The confidence coefficients for lines. |

## [iRegionOfInterest](auxiliary-regionofinterest.md)

```objc
@interface iRegionOfInterest
```

`RegionOfInterest` is one of the [`results`](auxiliary-intermediateresult.md#results) type in `IntermediateResult`.

| Attribute | Type | Description |
|---------- | ---- | ----------- |
| [`roiId`](#roiid) | *NSInteger* | The ID generated by the SDK. |
| [`point`](#point) | [`CGPoint`](auxiliaryiDBRPoint.md) | The left top point of the region. |
| [`width`](#width) | *NSInteger* | The width of the region. |
| [`height`](#height) | *NSInteger* | The height of the region. |

## [iLocalizationResult](auxiliary-localizationresult.md)

```objc
@interface iLocalizationResult
```

`LocalizationResult` can be the extension of the class [`IntermediateResult`](auxiliary-intermediateresult.md). It stores the localization result information.

| Attribute | Type | Description |
|---------- | ---- | ----------- |
| [`terminatePhase`](#terminatephase) | [`EnumTerminatePhase`]({{ site.enumerations }}parameter-mode-enums.html#terminatephase) | The terminate phase of localization result. |
| [`barcodeFormat`](#barcodeformat) | [`EnumBarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) | Barcode type in BarcodeFormat group 1. |
| [`barcodeFormatString`](#barcodeformatstring) | *NSString \** | Barcode type in BarcodeFormat group 1 as string. |
| [`barcodeFormat_2`](#barcodeformat_2 ) | [`EnumBarcodeFormat2`]({{ site.enumerations }}format-enums.html#barcodeformat_2) | Barcode type in BarcodeFormat group 2. |
| [`barcodeFormatString_2`](#barcodeformatstring_2) | *NSString \** | Barcode type in BarcodeFormat group 2 as string. |
| [`resultPoints`](#resultpoints) | *NSArray \** | The vertices coordinates information of the barcode region. |
| [`angle`](#angle) | *NSInteger* | The angle of a barcode. Values range is from 0 to 360. |
| [`moduleSize`](#modulesize) | *NSInteger* | The barcode module size (the minimum bar width in pixel). |
| [`pageNumber`](#pagenumber) | *NSInteger* | The page number the barcode located in. The index is 0-based. |
| [`regionName`](#regionname) | *NSString \** | The region name the barcode located in. |
| [`documentName`](#documentname)| *NSString \** | The document name. |
| [`resultCoordinateType`](#resultcoordinatetype) | [`EnumResultCoordinateType`]({{ site.enumerations }}result-enums.html#resultcoordinatetype) | The coordinate type. |
| [`accompanyingTextBytes`](#accompanyingtextbytes) | *NSData \** | The accompanying text content in a byte array. |
| [`accompanyingTextBytesLength`](#accompanyingtextbyteslength) | *NSInteger* | The length of the accompanying text byte array. |
| [`confidence`](#confidence) | *NSInteger* | The confidence of the localization result. |
