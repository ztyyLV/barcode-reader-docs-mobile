---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - QRCodeDetails Class
description: This page shows the QRCodeDetails Class of Dynamsoft Barcode Reader for Android SDK.
keywords: QRCodeDetails, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---


# QRCodeDetails

```java
import com.dynamsoft.dbr.QRCodeDetails;
```

`QRCodeDetails` is one of the [`detailedResult`](class-TextResult.md#detailedresult) in class `TextResult`. It stores the QRCode details.

## Attributes
  
| Attribute | Description |
|---------- | ---- |
| `int moduleSize` | The barcode module size (the minimum bar width in pixels). |
| `int rows`| The row count of the barcode.   |
| `int columns` | The column count of the barcode. |
| `int errorCorrectionLevel` | The error correction level of the barcode.   |
| `int version` | The version of the QR Code. |
| `int model` | Number of the models. |
| `int mode` | Identify the first data encoding mode. |
| `int page` | Identify the position of the particular symbol. |
| `int totalPage` | Identify the total number of symbols to be concatenated in the Structured Append format. |
| `int parityData` | The Parity Data shall be an 8 bit byte following the Symbol Sequence Indicator. The parity data is a value obtained by XORing byte by byte the ASCII/JIS values of all the original input data before division into symbol blocks. |

## Usage

```java
//The textresult[i] is one of the text results you got  
QRCodeDetails qrDetails = (QRCodeDetails) textresult[i].detailedResult;
int qr_ = qrDetails.moduleSize;
int qr_rows = qrDetails.rows;
int qr_columns = qrDetails.columns;
int qr_errorCorrectionLevel = qrDetails.errorCorrectionLevel;
int qr_version = qrDetails.version;
int qr_model = qrDetails.model;
int qr_mode = qrDetails.mode;
int qr_page = qrDetails.page;
int qr_totalPage = qrDetails.totalPage;
int qr_parityData = qrDetails.parityData;
```
