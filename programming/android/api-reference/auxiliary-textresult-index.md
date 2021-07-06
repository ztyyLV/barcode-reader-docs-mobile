---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - TextResult index
description: This page shows the TextResult index of Dynamsoft Barcode Reader for Android SDK.
keywords: TextResult index, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
---

# Barcode Result Classes

## Class [TextResult](auxiliary-TextResult.md)

```java
import com.dynamsoft.dbr.TextResult;
```

| Attribute | Type | Description |
|-----------|------| ----------- |
| `barcodeFormat` | *int* | Barcode type in BarcodeFormat group 1. |
| `barcodeFormatString` | *String* | Barcode type in BarcodeFormat group 1 as string. |
| `barcodeFormat_2` | *int* | Barcode type in BarcodeFormat group 2. |
| `barcodeFormatString_2` | *String* | Barcode type in BarcodeFormat group 2 as string. |
| `barcodeText` | *String* | The barcode text, ends by '\0'. |
| `barcodeBytes` | *byte\[\]* | The barcode content in a byte array. |
| `barcodeBytesLength`| *int* | The length of the byte array. |
| `localizationResult` | [`LocalizationResult`](auxiliary-LocalizationResult.md)\* | The corresponding localization result. |
| `detailedResult` | *Object* | One of the following: [`QRCodeDetails`](auxiliary-qrcodedetails.md), [`PDF417Details`](auxiliary-pdf417details.md), [`DataMatrixDetails`](auxiliary-datamatrixdetails.md), [`AztecDetails`](auxiliary-aztecdetails.md), [`OneDCodeDetails`](auxiliary-onedcodedetails.md). |
| `results` | [`ExtendedResult`](auxiliary-extendedresult.md)\[\] | The extended result array. |
| `exception` | *String* | The exception message. |
| `isDPM` | *int* | This attribute stands for whether the result is a DPM result. |
| `isMirrored` | *int* | This attribute stands for whether the barcode is mirrored. |

```java
// Get the text result by decode methodes
TextResult[] textresult = barcodeReader.decodeBuffer(frame.getData(),frame.getWidth(),frame.getHeight(),frame.getStrides()[0],frame.getFormat(),"");
```

## Class [LocalizationResult](auxiliary-LocalizationResult.md)

```java
import com.dynamsoft.dbr.LocalizationResult;
```

`LocalizationResult` is the extension of the class [`TextResult`](auxiliary-TextResult.md). It stores the localization result information.

| Attribute | Type | Description |
|---------- | ---- | ----------- |
| `terminatePhase` | *int* | The terminate phase of localization result. |
| `barcodeFormat` | *int* | Barcode type in BarcodeFormat group 1. |
| `barcodeFormatString` | *String* | Barcode type in BarcodeFormat group 1 as string. |
| `barcodeFormat_2` | *int* | Barcode type in BarcodeFormat group 2. |
| `barcodeFormatString_2` | *String* | Barcode type in BarcodeFormat group 2 as string. |
| `resultPoints` | [`Point`](auxiliary-Point.md)\[\] | The vertices coordinates information of the barcode region. |
| `angle` | *int* | The angle of a barcode. Values range is from 0 to 360. |
| `moduleSize` | *int* | The barcode module size (the minimum bar width in pixel). |
| `pageNumber` | *int* | The page number the barcode located in. The index is 0-based. |
| `regionName` | *String* | The region name the barcode located in. |
| `documentName` | *String* | The document name. |
| `resultCoordinateType` | *int* | The coordinate type. |
| `accompanyingTextBytes` | *byte\[\]* | The accompanying text content in a byte array. |
| `confidence` | *int* | The confidence of the localization result. |

```java
if ( textresult != null && textresult.length != 0){
    for ( int i = 0; i< textresult.length; i++ ) {
        LocalizationResult localizationResult = textresult[i].localizationResult;
        // DO something on localization results.
    }
}
```

## Class [ExtendedResult](auxiliary-ExtendedResult.md)

```java
import com.dynamsoft.dbr.ExtendedResult;
```

`ExtendedResult` is the extension of the class [`TextResult`](auxiliary-TextResult.md). It stores the extended result information.
  
| Attribute | Type | Description |
|---------- |------|-------------|
| `resultType` | *int* | The extended result type. |
| `barcodeFormat` | *int* | Barcode type in BarcodeFormat group 1. |
| `barcodeFormatString` | *String* | Barcode type in BarcodeFormat group 1 as string. |
| `barcodeFormat_2` | *int* | Barcode type in BarcodeFormat group 2. |
| `barcodeFormatString_2` | *String* | Barcode type in BarcodeFormat group 2 as string. |
| `confidence` | *int* | The confidence of the result. The higher confidence means the higher accuracy. |
| `bytes` | *byte\[\]* | The content in a byte array. |
| `accompanyingTextBytes` | *byte\[\]* | The accompanying text content in a byte array. |
| `deformation` | *int* | The deformation value. |
| `detailedResult` | *Object* | One of the following: [`QRCodeDetails`](auxiliary-qrcodedetails.md), [`PDF417Details`](auxiliary-pdf417details.md), [`DataMatrixDetails`](auxiliary-datamatrixdetails.md), [`AztecDetails`](auxiliary-aztecdetails.md), [`OneDCodeDetails`](auxiliary-onedcodedetails.md). |
| `samplingImage` | [`SamplingImageData`](auxiliary-samplingimagedata.md) | The sampling image info. |
| `clarity` | *int* | The clarity of the barcode zone in percentage. |

```java
if ( textresult != null && textresult.length != 0){
    for ( int i = 0; i < textresult.length; i++ ) {
        ExtendedResult[] extendedResult = textresult[i].results;
        // Do something on extended results.
    }
}
```

## Class [AztecDetails](auxiliary-AztecDetails.md)

```java
import com.dynamsoft.dbr.AztecDetails;
```

`AztecDetails` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the Aztec code details.
  
| Attribute | Type | Description |
|---------- | -----|------ |
| `moduleSize`| *int* | The barcode module size (the minimum bar width in pixel). |
| `rows` | *int* | The row count of the barcode. |
| `columns` | *int* | The column count of the barcode. |
| `layerNumber` | *int* | A negative number (-1, -2, -3, -4) specifies a compact Aztec code. A positive number (1, 2, .. 32) specifies a normal (full-rang) Aztec code. |

```java
//The textresult[i] is one of the text result you got  
AztecDetails aztecDetails = (AztecDetails) textresult[i].detailedResult;
```

## Class [DataMatrixDetails](auxiliary-DataMatrixDetails.md)

```java
import com.dynamsoft.dbr.DataMatrixDetails;
```

`DataMatrixDetails` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the DataMatrix code details.
  
| Attribute | Type | Description |
|---------- |-----|------|
| `moduleSize` | *int* | The barcode module size (the minimum bar width in pixel). |
| `rows`| *int* | The row count of the barcode. |
| `columns` | *int* | The column count of the barcode. |
| `dataRegionRows` | *int* | The data region row count of the barcode. |
| `dataRegionColumns` | *int* | The data region column count of the barcode. |
| `dataRegionNumber` | *int* | The data region count. |

```java
//The textresult[i] is one of the text result you got  
DataMatrixDetails dataMatrixDetails = (DataMatrixDetails) textresult[i].detailedResult;
```

## Class [OneDCodeDetails](auxiliary-OneDCodeDetails.md)

```java
import com.dynamsoft.dbr.OneDCodeDetails;
```

`OneDCodeDetails` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the OneD code details.

| Attribute | Type | Description |
|---------- |-----| ---- |
| `moduleSize` | *int* | The barcode module size (the minimum bar width in pixel). |
| `startCharsBytes` | *int* | The start chars in a byte array. |
| `stopCharsBytes` | *int* | The stop chars in a byte array. |
| `checkDigitBytes` | *int* | The check digit chars in a byte array. |
| `startPatternRange` | *int* | The start pattern range of the OneDcode. |
| `middlePatternRange` | *int* | The middle pattern range of the OneDcode. |
| `endPatternRange` | *int* | The end pattern range of the OneDcode. |

```java
//The textresult[i] is one of the text result you got  
OneDCodeDetails oneDDetails = (OneDCodeDetails) textresult[i].detailedResult;
```

## Class [PDF417Details](auxiliary-PDF417Details.md)

```java
import com.dynamsoft.dbr.PDF417Details;
```

`PDF417Details` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the PDF417 code details.
  
| Attribute | Type | Description |
|---------- |------|------------ |
| `moduleSize` | *int* | The barcode module size (the minimum bar width in pixel). |
| `rows` | *int* | The row count of the barcode. |
| `columns` | *int* | The column count of the barcode. |
| `errorCorrectionLevel` | *int* | The error correction level of the barcode. |

```java
//The textresult[i] is one of the text results you got  
PDF417Details pdf417Details = (PDF417Details) textresult[i].detailedResult;
```

## Class [QRCodeDetails](auxiliary-QRCodeDetails.md)

```java
import com.dynamsoft.dbr.QRCodeDetails;
```

`QRCodeDetails` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the QRCode details.
  
| Attribute | Type | Description |
|---------- | ---- |-----|
| `moduleSize` | *int* | The barcode module size (the minimum bar width in pixels). |
| `rows`| *int* | The row count of the barcode.   |
| `columns` | *int* | The column count of the barcode. |
| `errorCorrectionLevel` | *int* | The error correction level of the barcode.   |
| `version` | *int* | The version of the QR Code. |
| `model` | *int* | Number of the models. |
| `mode` | *int* | Identify the first data encoding mode. |
| `page` | *int* | Identify the position of the particular symbol. |
| `totalPage` | *int* | Identify the total number of symbols to be concatenated in the Structured Append format. |
| `parityData` | *int* | The Parity Data shall be an 8 bit byte following the Symbol Sequence Indicator. The parity data is a value obtained by XORing byte by byte the ASCII/JIS values of all the original input data before division into symbol blocks. |

```java
//The textresult[i] is one of the text results you got  
QRCodeDetails qrDetails = (QRCodeDetails) textresult[i].detailedResult;
```

## Class [SamplingImageData](auxiliary-samplingimagedata.md)

```java
import com.dynamsoft.dbr.SamplingImageData;
```

`SamplingImageData` stores the detailed image data in `ExtendedResult`.

| Attribute | Type | Description |
|---------- | ---- | ----------- |
| [`bytes`](#bytes) | *byte\[\]* | The sampling image data in a byte array. |
| [`width`](#width) | *int* | The width of the sampling image. |
| [`height`](#height) | *int* | The height of the sampling image. |

```java
SamplingImageData samplingImageData = extendedResult[j].samplingImage;
```
