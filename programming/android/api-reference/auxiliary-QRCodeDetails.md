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

## moduleSize

The barcode module size (the minimum bar width in pixels).

```java
int com.dynamsoft.dbr.QRCodeDetails.moduleSize
```

## rows

The row count of the barcode.  

```java
int com.dynamsoft.dbr.QRCodeDetails.rows
```

## columns

The column count of the barcode.

```java
int com.dynamsoft.dbr.QRCodeDetails.columns
```

## errorCorrectionLevel

The error correction level of the barcode.  

```java
int com.dynamsoft.dbr.QRCodeDetails.errorCorrectionLevel
```

## version

The version of the QR Code.

```java
int com.dynamsoft.dbr.QRCodeDetails.version
```

## model

Number of the models.

```java
int com.dynamsoft.dbr.QRCodeDetails.model
```

## mode

Identify the first data encoding mode.

```java
int com.dynamsoft.dbr.QRCodeDetails.mode
```

## page

Identify the position of the particular symbol.

```java
int com.dynamsoft.dbr.QRCodeDetails.page
```

## totalPage

Identify the total number of symbols to be concatenated in the Structured Append format.

```java
int com.dynamsoft.dbr.QRCodeDetails.totalPage
```

## parityData

The Parity Data shall be an 8 bit byte following the Symbol Sequence Indicator. The parity data is a value obtained by XORing byte by byte the ASCII/JIS values of all the original input data before division into symbol blocks.

```java
byte com.dynamsoft.dbr.QRCodeDetails.parityData
```
