---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - DataMatrixDetails Class
description: This page shows the DataMatrixDetails Class of Dynamsoft Barcode Reader for Android SDK.
keywords: DataMatrixDetails, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---

# Class DataMatrixDetails

```java
import com.dynamsoft.dbr.DataMatrixDetails;
```

`DataMatrixDetails` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the DataMatrix code details.

## Attributes
  
| Attribute | Type | Description |
|---------- |-----|------|
| `moduleSize` | *int* | The barcode module size (the minimum bar width in pixel). |
| `rows`| *int* | The row count of the barcode. |
| `columns` | *int* | The column count of the barcode. |
| `dataRegionRows` | *int* | The data region row count of the barcode. |
| `dataRegionColumns` | *int* | The data region column count of the barcode. |
| `dataRegionNumber` | *int* | The data region count. |

## Usage

```java
//The textresult[i] is one of the text results you got  
DataMatrixDetails dataMatrixDetails = (DataMatrixDetails) textresult[i].detailedResult;
int dm_moduleSize = dataMatrixDetails.moduleSize;
int dm_columns = dataMatrixDetails.columns;
int dm_rows = dataMatrixDetails.rows;
int dm_dataRegionRows = dataMatrixDetails.dataRegionRows;
int dm_dataRegionColumns = dataMatrixDetails.dataRegionColumns;
int dm_dataRegionNumber = dataMatrixDetails.dataRegionNumber;
```
