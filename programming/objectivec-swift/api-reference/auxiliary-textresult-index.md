---
layout: default-layout
title: Dynamsoft Barcode Reader iOS API Reference - TextResult index
description: This page shows the TextResult index of Dynamsoft Barcode Reader for iOS SDK.
keywords: TextResult index, api reference, iOS
needAutoGenerateSidebar: true
---

# Barcode Result Classes

## [iTextResult](auxiliary-iTextResult.md)

```objc
@interface iTextResult
```  

| Attribute | Type | Description |
|-----------|------| ----------- |
| `barcodeFormat` | [`EnumBarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) | Barcode type in BarcodeFormat group 1. |
| `barcodeFormatString` | *NSString \** | Barcode type in BarcodeFormat group 1 as string. |
| `barcodeFormat_2` | [`EnumBarcodeFormat2`]({{ site.enumerations }}format-enums.html#barcodeformat_2) | Barcode type in BarcodeFormat group 2. |
| `barcodeFormatString_2` | *NSString \** | Barcode type in BarcodeFormat group 2 as string. |
| `barcodeText` | *NSString \** | The barcode text, ends by '\0'. |
| `barcodeBytes` | *NSData \** | The barcode content in a byte array. |
| `localizationResult` | [`iLocalizationResult`](auxiliary-iLocalizationResult.md)\* | The corresponding localization result. |
| `detailedResult` | *NSObject \** | One of the following: [`QRCodeDetails`](#qrcodedetails), [`PDF417Details`](#pdf417details), [`DataMatrixDetails`](#datamatrixdetails), [`AztecDetails`](#aztecdetails), [`OneDCodeDetails`](#onedcodedetails). |
| `extendedResults` | [`NSArray<iExtendedResult*>*`](auxiliary-iExtendedResult.md)\* | The extended result array. |
| `exception` | *NSString \** | The exception message. |
| `isDPM` | *NSInteger* | This attribute stands for whether the result is a DPM result. |
| `isMirrored` | *NSInteger* | This attribute stands for whether the barcode is mirrored. |

## [iLocalizationResult](auxiliary-iLocalizationResult.md)

```objc
@interface iLocalizationResult
```  

`LocalizationResult` is the extension of the class [`TextResult`](auxiliary-TextResult.md). It stores the localization result information.

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

## [iExtendedResult](auxiliary-iExtendedResult.md)

```objc
@interface iExtendedResult
```  

`ExtendedResult` is the extension of the class [`TextResult`](auxiliary-TextResult.md). It stores the extended result information.
  
| Attribute | Type | Description |
|---------- |------|-------------|
| [`resultType`](#resulttype) | [`EnumResultType`]({{ site.enumerations }}result-enums.html#resulttype) | The extended result type. |
| [`barcodeFormat`](#barcodeformat) | [`EnumBarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) | Barcode type in BarcodeFormat group 1. |
| [`barcodeFormatString`](#barcodeformatstring) | *NSString \** | Barcode type in BarcodeFormat group 1 as string. |
| [`barcodeFormat_2`](#barcodeformat_2) | [`EnumBarcodeFormat2`]({{ site.enumerations }}format-enums.html#barcodeformat_2) | Barcode type in BarcodeFormat group 2. |
| [`barcodeFormatString_2`](#barcodeformatstring_2) | *NSString \** | Barcode type in BarcodeFormat group 2 as string. |
| [`confidence`](#confidence) | *NSInteger* | The confidence of the result. The higher confidence means the higher accuracy. |
| [`bytes`](#bytes) | *NSData \** | The content in a byte array. |
| [`bytesLength`](#byteslength) | *NSInteger* | The length of the byte array. |
| [`accompanyingTextBytes`](#accompanyingtextbytes) | *NSData \** | The accompanying text content in a byte array. |
| [`accompanyingTextBytesLength`](#accompanyingtextbyteslength) | *NSInteger* | The length of the accompanying text byte array. |
| [`deformation`](#deformation) | *NSInteger* | The deformation value. |
| [`detailedResult`](#detailedresult) | *NSObject \** | One of the following: [`QRCodeDetails`](#qrcodedetails), [`PDF417Details`](#pdf417details), [`DataMatrixDetails`](#datamatrixdetails), [`AztecDetails`](#aztecdetails), [`OneDCodeDetails`](#onedcodedetails). |
| [`samplingImage`](#samplingimage) | [`iSamplingImageData*`](auxiliary-iSamplingImageData.md) | The sampling image info. |
| [`clarity`](#clarity) | *NSInteger* | The clarity of the barcode zone in percentage. |

## [iAztecDetails](auxiliary-iAztecDetails.md)

```objc
@interface iAztecDetails
```

`AztecDetails` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the Aztec code details.
  
| Attribute | Type | Description |
|---------- | -----|------ |
| [`moduleSize`](#modulesize) | *NSInteger* | The barcode module size (the minimum bar width in pixel). |
| [`rows`](#rows) | *NSInteger* | The row count of the barcode. |
| [`columns`](#columns) | *NSInteger* | The column count of the barcode. |
| [`layerNumber`](#layernumber) | *NSInteger* | A negative number (-1, -2, -3, -4) specifies a compact Aztec code. A positive number (1, 2, .. 32) specifies a normal (full-rang) Aztec code. |

## [iDataMatrixDetails](auxiliary-iDataMatrixDetails.md)

```objc
@interface iDataMatrixDetails
```  

`DataMatrixDetails` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the DataMatrix code details.
  
| Attribute | Type | Description |
|---------- |-----|------|
| [`moduleSize`](#modulesize) | *NSInteger* | The barcode module size (the minimum bar width in pixel). |
| [`rows`](#rows) | *NSInteger* | The row count of the barcode. |
| [`columns`](#columns) | *NSInteger* | The column count of the barcode. |
| [`dataRegionRows`](#dataregionrows) | *NSInteger* | The data region row count of the barcode. |
| [`dataRegionColumns`](#dataregioncolumns) | *NSInteger* | The data region column count of the barcode. |
| [`dataRegionNumber`](#dataregionnumber) | *NSInteger* | The data region count. |

## [iOneDCodeDetails](auxiliary-iOneDCodeDetails.md)

```objc
@interface iOneDCodeDetails
```  

`OneDCodeDetails` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the OneD code details.

| Attribute | Type | Description |
|---------- |-----| ---- |
| [`moduleSize`](#modulesize) | *NSInteger* | The barcode module size (the minimum bar width in pixel). |
| [`startCharsBytes`](#startcharsbytes) | *NSData \** | The start chars in a byte array. |
| [`startCharsBytesLength`](#startcharsbyteslength) | *NSInteger* | The length of the start chars byte array. |
| [`stopCharsBytes`](#stopcharsbytes) | *NSData \** | The stop chars in a byte array. |
| [`stopCharsBytesLength`](#stopcharsbyteslength) | *NSInteger* | The length of the stop chars byte array. |
| [`checkDigitBytes`](#checkdigitbytes) | *NSData \** | The check digit chars in a byte array. |
| [`checkDigitBytesLength`](#checkdigitbyteslength) | *NSInteger* | The length of the check digit chars byte array. |

## [iPDF417Details](auxiliary-iPDF417Details.md)

```objc
@interface iPDF417Details
```

`PDF417Details` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the PDF417 code details.
  
| Attribute | Type | Description |
|---------- |------|------------ |
| [`moduleSize`](#modulesize) | *NSInteger* | The barcode module size (the minimum bar width in pixel). |
| [`rows`](#rows) | *NSInteger* | The row count of the barcode. |
| [`columns`](#columns) | *NSInteger* | The column count of the barcode. |
| [`errorCorrectionLevel`](#errorcorrectionlevel) | *NSInteger* | The error correction level of the barcode. |

## [iQRCodeDetails](auxiliary-iQRCodeDetails.md)

```objc
@interface iQRCodeDetails
```  

`QRCodeDetails` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the QRCode details.
  
| Attribute | Type | Description |
|---------- | ---- |-----|
| [`moduleSize`](#modulesize) | *NSInteger* | The barcode module size (the minimum bar width in pixels). |
| [`rows`](#rows) | *NSInteger* | The row count of the barcode.   |
| [`columns`](#columns) | *NSInteger* | The column count of the barcode. |
| [`errorCorrectionLevel`](#errorcorrectionlevel) | *NSInteger* | The error correction level of the barcode.   |
| [`version`](#version) | *NSInteger* | The version of the QR Code. |
| [`model`](#model) | *NSInteger* | Number of the models. |
| [`mode`](#mode) | *NSInteger* | Identify the first data encoding mode. |
| [`page`](#page) | *NSInteger* | Identify the position of the particular symbol. |
| [`totalPage`](#totalpage) | *NSInteger* | Identify the total number of symbols to be concatenated in the Structured Append format. |
| [`parityData`](#paritydata) | *byte* | The Parity Data shall be an 8 bit byte following the Symbol Sequence Indicator. The parity data is a value obtained by XORing byte by byte the ASCII/JIS values of all the original input data before division into symbol blocks. |

## [iSamplingImageData](auxiliary-iSamplingImageData.md)

```objc
@interface iSamplingImageData
```  

`SamplingImageData` stores the detailed image data in `ExtendedResult`.

| Attribute | Type | Description |
|---------- | ---- | ----------- |
| [`bytes`](#bytes) | *NSData\** | The sampling image data in a byte array. |
| [`width`](#width) | *NSInteger* | The width of the sampling image. |
| [`height`](#height) | *NSInteger* | The height of the sampling image. |
