---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - QRCodeDetails Class
description: This page shows the QRCodeDetails Class of Dynamsoft Barcode Reader for Android SDK.
keywords: QRCodeDetails, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---


# Class QRCodeDetails

```java
import com.dynamsoft.dbr.QRCodeDetails;
```

`QRCodeDetails` is one of the [`detailedResult`](class-TextResult.md#detailedresult) in class `TextResult`. It stores the QRCode details.

| Attribute | Type |
|---------- | ---- |
| `moduleSize` | *int* |
| `rows`| *int* |
| `columns` | *int* |
| `errorCorrectionLevel` | *int* |
| `version` | *int* |
| `model` | *int* |
| `mode` | *int* |
| `page` | *int* |
| `totalPage` | *int* |
| `parityData` | *int* |

## moduleSize

The barcode module size (the minimum bar width in pixels).

```java
int moduleSize
```

## rows

The row count of the barcode.  

```java
int rows
```

## columns

The column count of the barcode.

```java
int columns
```

## errorCorrectionLevel

The error correction level of the barcode.  

```java
int errorCorrectionLevel
```

## version

The version of the QR Code.

```java
int version
```

## model

Number of the models.

```java
int model
```

## mode

Identify the first data encoding mode.

```java
int mode
```

## page

Identify the position of the particular symbol.

```java
int page
```

## totalPage

Identify the total number of symbols to be concatenated in the Structured Append format.

```java
int totalPage
```

## parityData

The Parity Data shall be an 8 bit byte following the Symbol Sequence Indicator. The parity data is a value obtained by XORing byte by byte the ASCII/JIS values of all the original input data before division into symbol blocks.

```java
byte parityData
```
