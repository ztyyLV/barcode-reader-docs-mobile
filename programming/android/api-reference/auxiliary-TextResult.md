---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - TextResult Class
description: This page shows the TextResult Class of Dynamsoft Barcode Reader for Android SDK.
keywords: TextResult, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---

# Class TextResult

Stores the text result.

| Attribute | Type |
|-----------|------|
| [`barcodeFormat`](#barcodeformat) | *int* |
| [`barcodeFormatString`](#barcodeformatstring) | *String* |
| [`barcodeFormat_2`](#barcodeformat_2) | *int* |
| [`barcodeFormatString_2`](#barcodeformatstring_2) | *String* |
| [`barcodeText`](#barcodetext) | *String* |
| [`barcodeBytes`](#barcodebytes) | *byte\[\]* |
| [`localizationResult`](#localizationresult) | [`LocalizationResult`](auxiliary-LocalizationResult.md)\* |
| [`detailedResult`](#detailedresult) | *Object* |
| [`results`](#results) | [`ExtendedResult`](auxiliary-ExtendedResult.md)\[\] |
| [`exception`](#exception) | *String* |
| [`isDPM`](#isdpm) | *int* |
| [`isMirrored`](#ismirrored) | *int* |

## barcodeFormat

Barcode type in BarcodeFormat group 1.

```java
int barcodeFormat
```

Read more in [`Enumerations: BarcodeFormatIds`]({{ site.enumerations }}format-enums.html#barcodeformat)

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

Read more in [`Enumerations: BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat)

## barcodeFormatString_2

Barcode type in BarcodeFormat group 2 as string.

```java
String barcodeFormatString_2
```

## barcodeText

The barcode text, ends by '\0'.

```java
String barcodeText
```

## barcodeBytes

The barcode content in a byte array.

```java
byte[] barcodeBytes
```

## barcodeBytesLength

The length of the byte array.

```java
int barcodeBytesLength
```

## localizationResult

The corresponding localization result.

```java
LocalizationResult localizationResult
```

## detailedResult

One of the following: [`QRCodeDetails`](auxiliary-QRCodeDetails.md), [`PDF417Details`](auxiliary-PDF417Details.md), [`DataMatrixDetails`](auxiliary-DataMatrixDetails.md), [`AztecDetails`](auxiliary-AztecDetails.md), [`OneDCodeDetails`](auxiliary-OneDCodeDetails.md).

```java
Object detailedResult
```

## results

The extended result array.

```java
ExtendedResult[] results
```

## exception

The exception message.

```java
String exception
```

## isDPM

This attribute stands for whether the result is a DPM result.

```java
int isDPM
```

## isMirrored

This attribute stands for whether the barcode is mirrored.

```java
int isMirrored
```
