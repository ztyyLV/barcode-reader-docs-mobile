---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - PDF417Details Class
description: This page shows the PDF417Details Class of Dynamsoft Barcode Reader for Android SDK.
keywords: PDF417Details, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---


# Class PDF417Details

```java
import com.dynamsoft.dbr.PDF417Details;
```

`PDF417Details` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the PDF417 code details.
  
## Attributes
  
| Attribute | Type | Description |
|---------- |------|------------ |
| `moduleSize` | *int* | The barcode module size (the minimum bar width in pixel). |
| `rows` | *int* | The row count of the barcode. |
| `columns` | *int* | The column count of the barcode. |
| `errorCorrectionLevel` | *int* | The error correction level of the barcode. |

## Usage

```java
//The textresult[i] is one of the text results you got  
PDF417Details pdf417Details = (PDF417Details) textresult[i].detailedResult;
int pdf417_moduleSize = pdf417Details.moduleSize;
int pdf417_rows = pdf417Details.rows;
int pdf417_columns = pdf417Details.columns;
int pdf417_errorCorrectionLevel = pdf417Details.errorCorrectionLevel;
```
