---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - LocalizationResult Class
description: This page shows the LocalizationResult Class of Dynamsoft Barcode Reader for Android SDK.
keywords: LocalizationResult, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
---


# Class LocalizationResult

The `LocalizationResult` extends the class [`TextResult`](auxiliary-TextResult.md) and [`IntermediateResult`](auxiliary-IntermediateResult.md). It stores the barcode localization data.

| Attribute | Type | Description |
|---------- | ---- | ----------- |
| [`terminatePhase`](#terminatephase) | *int* | The terminate phase of localization result. |
| [`barcodeFormat`](#barcodeformat) | *int* | Barcode type in BarcodeFormat group 1. |
| [`barcodeFormatString`](#barcodeformatstring) | *String* | Barcode type in BarcodeFormat group 1 as string. |
| [`barcodeFormat_2`](#barcodeformat_2 ) | *int* | Barcode type in BarcodeFormat group 2. |
| [`barcodeFormatString_2`](#barcodeformatstring_2) | *String* | Barcode type in BarcodeFormat group 2 as string. |
| [`resultPoints`](#resultpoints) | [`Point`](auxiliary-Point.md)\[\] | The vertices coordinates information of the barcode region. |
| [`angle`](#angle) | *int* | The angle of a barcode. Values range is from 0 to 360. |
| [`moduleSize`](#modulesize) | *int* | The barcode module size (the minimum bar width in pixel). |
| [`pageNumber`](#pagenumber) | *int* | The page number the barcode located in. The index is 0-based. |
| [`regionName`](#regionname) | *String* | The region name the barcode located in. |
| [`documentName`](#documentname)| *String* | The document name. |
| [`resultCoordinateType`](#resultcoordinatetype) | *int* | The coordinate type. |
| [`accompanyingTextBytes`](#accompanyingtextbytes) | *byte\[\]* | The accompanying text content in a byte array. |
| [`confidence`](#confidence) | *int* | The confidence of the localization result. |

## terminatePhase

The terminate phase of localization result.

```java
int terminatePhase
```

## barcodeFormat

Barcode type in BarcodeFormat group 1.

```java
int barcodeFormat
```

## barcodeFormatString

Barcode type in BarcodeFormat group 1 as string.

```java
String barcodeFormatString
```

## barcodeFormat_2

Barcode type in BarcodeFormat group 2.

```java
int barcodeFormat_2
```

## barcodeFormatString_2

Barcode type in BarcodeFormat group 2 as string.

```java
String barcodeFormatString_2
```

## resultPoints

The vertices coordinates information of the barcode region.

```java
Point[] resultPoints
```

## angle

The angle of a barcode. Values range is from 0 to 360.

```java
int angle
```

## moduleSize

The barcode module size (the minimum bar width in pixel).

```java
int moduleSize
```

## pageNumber

The page number the barcode located in. The index is 0-based.

```java
int pageNumber
```

## regionName

The region name the barcode located in.

```java
String regionName
```

## documentName

The document name.

```java
String documentName
```

## resultCoordinateType

The coordinate type.

```java
int resultCoordinateType
```

## accompanyingTextBytes

The accompanying text content in a byte array.

```java
byte[] accompanyingTextBytes
```

## confidence

The confidence of the localization result.

```java
int confidence
```
