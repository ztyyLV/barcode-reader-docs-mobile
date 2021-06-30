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

`PDF417Details` is one of the [`detailedResult`](class-TextResult.md#detailedresult) in class `TextResult`. It stores the PDF417 code details.
  
## Attributes
  
| Attribute | Description |
|---------- | ---- |
| `int moduleSize` | The barcode module size (the minimum bar width in pixel). |
| `int rows` | The row count of the barcode. |
| `int columns` | The column count of the barcode. |
| `int errorCorrectionLevel` | The error correction level of the barcode. |

## Usage

```java
//The textresult[i] is one of the text results you got  
PDF417Details pdf417Details = (PDF417Details) textresult[i].detailedResult;
int pdf417_moduleSize = pdf417Details.moduleSize;
int pdf417_rows = pdf417Details.rows;
int pdf417_columns = pdf417Details.columns;
int pdf417_errorCorrectionLevel = pdf417Details.errorCorrectionLevel;
```
