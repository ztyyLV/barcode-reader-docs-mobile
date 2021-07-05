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

| Attribute | Type |
|---------- | ---- |
| [`moduleSize`](#modulesize) | *int* |
| [`rows`](#rows) | *int* |
| [`columns`](#columns) | *int* |
| [`dataRegionRows`](#dataregionrows) | *int* |
| [`dataRegionColumns`](#dataregioncolumns) | *int* |
| [`dataRegionNumber`](#dataregionnumber) | *int* |

## moduleSize

The barcode module size (the minimum bar width in pixel).

```java
int com.dynamsoft.dbr.DataMatrixDetails.moduleSize
```

## rows

The row count of the barcode.

```java
int com.dynamsoft.dbr.DataMatrixDetails.rows
```

## columns

The column count of the barcode.

```java
int com.dynamsoft.dbr.DataMatrixDetails.columns
```

## dataRegionRows

The data region row count of the barcode.

```java
int com.dynamsoft.dbr.DataMatrixDetails.dataRegionRows
```

## dataRegionColumns

The data region column count of the barcode.

```java
int com.dynamsoft.dbr.DataMatrixDetails.dataRegionColumns
```

## dataRegionNumber

The data region count.

```java
int com.dynamsoft.dbr.DataMatrixDetails.dataRegionNumber
```
