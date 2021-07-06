---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - iPDF417Details Class
description: This page shows the iPDF417Details Class of Dynamsoft Barcode Reader for iOS SDK.
keywords: iPDF417Details, class, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
---


# Class iPDF417Details

`iPDF417Details` is one of the [`detailedResult`](auxiliary-iTextResult.md#detailedresult) in class `iTextResult`. It stores the PDF417 code details.

## Typedefs

```objc
@interface iPDF417Details
```  

| Attribute | Type |
|---------- | ---- |
| [`moduleSize`](#modulesize) | *NSInteger* |
| [`rows`](#rows) | *NSInteger* |
| [`columns`](#columns) | *NSInteger* |
| [`errorCorrectionLevel`](#errorcorrectionlevel) | *NSInteger* |

## moduleSize

The barcode module size (the minimum bar width in pixel).

```objc
NSInteger moduleSize
```

## rows

The row count of the barcode.

```objc
NSInteger rows
```

## columns

The column count of the barcode.

```objc
NSInteger columns
```

## errorCorrectionLevel

The error correction level of the barcode.

```objc
NSInteger errorCorrectionLevel
```
