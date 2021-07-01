---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - ExtendedResult Class
description: This page shows the ExtendedResult Class of Dynamsoft Barcode Reader for Android SDK.
keywords: ExtendedResult, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---


# ExtendedResult

`ExtendedResult` is the extension of the class [`TextResult`](auxiliary-TextResult.md). It stores the extended result information.

## Attributes
  
| Attribute | Type |
|---------- | ---- |
| [`resultType`](#resulttype) | *int* |
| [`barcodeFormat`](#barcodeformat) | *int* |
| [`barcodeFormatString`](#barcodeformatstring) | *String* |
| [`barcodeFormat_2`](#barcodeformat_2) | *int* |
| [`barcodeFormatString_2`](#barcodeformatstring_2) | *String* |
| [`confidence`](#confidence) | *int* |
| [`bytes`](#bytes) | *byte\[\]* |
| [`accompanyingTextBytes`](#accompanyingtextbytes) | *byte\[\]* |
| [`deformation`](#deformation) | *int* |
| [`detailedResult`](#detailedresult) | *Object* |
| [`samplingImage`](#samplingimage) | [`SamplingImageData`](SamplingImageData.md) |
| [`clarity`](#clarity) | *int* |

### resultType

Extended result type.

```java
int com.dynamsoft.dbr.ExtendedResult.resultType
```

### barcodeFormat

Barcode type in BarcodeFormat group 1.

```java
int com.dynamsoft.dbr.ExtendedResult.barcodeFormat
```

### barcodeFormatString

Barcode type in BarcodeFormat group 1 as string.

```java
String com.dynamsoft.dbr.ExtendedResult.barcodeFormatString
```

### barcodeFormat_2

Barcode type in BarcodeFormat group 2.

```java
int com.dynamsoft.dbr.ExtendedResult.barcodeFormat_2
```

### barcodeFormatString_2

Barcode type in BarcodeFormat group 2 as string.

```java
String com.dynamsoft.dbr.ExtendedResult.barcodeFormatString_2
```

### confidence

The confidence of the result. The higher confidence means the higher accuracy.

```java
int com.dynamsoft.dbr.ExtendedResult.confidence
```

### bytes

The content in a byte array.

```java
byte[] com.dynamsoft.dbr.ExtendedResult.bytes
```

### accompanyingTextBytes

The accompanying text content in a byte array.

```java
byte[] com.dynamsoft.dbr.ExtendedResult.accompanyingTextBytes
```

### deformation

The deformation value.

```java
int com.dynamsoft.dbr.ExtendedResult.deformation
```

### detailedResult

One of the following: [`QRCodeDetails`](auxiliary-QRCodeDetails.md), [`PDF417Details`](auxiliary-PDF417Details.md), [`DataMatrixDetails`](auxiliary-DataMatrixDetails.md), [`AztecDetails`](auxiliary-AztecDetails.md), [`OneDCodeDetails`](auxiliary-OneDCodeDetails.md).

```java
Object com.dynamsoft.dbr.ExtendedResult.detailedResult
```

### samplingImage

The sampling image info.

```java
SamplingImageData com.dynamsoft.dbr.ExtendedResult.samplingImage
```

### clarity

The clarity of the barcode zone in percentage.

```java
int com.dynamsoft.dbr.ExtendedResult.clarity
```
