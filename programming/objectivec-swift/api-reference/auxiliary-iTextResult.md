---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - iTextResult Class
description: This page shows the iTextResult Class of Dynamsoft Barcode Reader for iOS SDK.
keywords: iTextResult, class, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
---

# Class iTextResult

Stores the text result.

## Typedefs

```objc
@interface iTextResult
```  

| Attribute | Type | Description |
|-----------|------| ----------- |
| `barcodeFormat` | [`EnumBarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) | Barcode type in BarcodeFormat group 1. |
| `barcodeFormatString` | *NSString \** | Barcode type in BarcodeFormat group 1 as string. |
| `barcodeFormat_2` | [`EnumBarcodeFormat2`]({{ site.enumerations }}format-enums.html#barcodeformat_2) | Barcode type in BarcodeFormat group 2. |
| `barcodeFormatString_2` | *NSString \** | Barcode type in BarcodeFormat group 2 as string. |
| `barcodeText` | *NSString \** | The barcode text, ends by '\0'. |
| `barcodeBytes` | *NSData \** | The barcode content in a byte array. |
| `localizationResult` | [`iLocalizationResult`](auxiliary-iLocalizationResult.md) | The corresponding localization result. |
| `detailedResult` | *NSObject \** | One of the following: [`iQRCodeDetails`](auxiliary-iQRCodeDetails.md), [`iPDF417Details`](auxiliary-iPDF417Details.md), [`iDataMatrixDetails`](auxiliary-iDataMatrixDetails.md), [`iAztecDetails`](auxiliary-iAztecDetails.md), [`iOneDCodeDetails`](auxiliary-iOneDCodeDetails.md). |
| `extendedResults` | [`NSArray<iExtendedResult>`](auxiliary-iExtendedResult.md) | The extended result array. |
| `exception` | *NSString \** | The exception message. |
| `isDPM` | *NSInteger* | This attribute stands for whether the result is a DPM result. |
| `isMirrored` | *NSInteger* | This attribute stands for whether the barcode is mirrored. |

## barcodeFormat

Barcode type in BarcodeFormat group 1.

```objc
EnumBarcodeFormat barcodeFormat
```

## barcodeFormatString

Barcode type in BarcodeFormat group 1 as string.

```objc
NSString* barcodeFormatString
```

## barcodeFormat_2

Barcode type in BarcodeFormat group 2.

```objc
EnumBarcodeFormat2 barcodeFormat_2
```

## barcodeFormatString_2

Barcode type in BarcodeFormat group 2 as string.

```objc
NSString* barcodeFormatString_2
```

## barcodeText

The barcode text, ends by '\0'.

```objc
NSString* barcodeText
```

## barcodeBytes

The barcode content in a byte array.

```objc
NSData* barcodeBytes
```

## localizationResult

The corresponding localization result.

```objc
iLocalizationResult* localizationResult
```

## detailedResult

One of the following: [`iQRCodeDetails`](iQRCodeDetails.md), [`iPDF417Details`](iPDF417Details.md), [`iDataMatrixDetails`](iDataMatrixDetails.md), [`iAztecDetails`](iAztecDetails.md), [`iOneDCodeDetails`](iOneDCodeDetails.md).

```objc
NSObject* detailedResult
```

## extendedResults

The extended result array.

```objc
NSArray<iExtendedResult*>* extendedResults
```

## exception

The exception message.

```objc
NSString* exception
```

## isDPM

This attribute stands for whether the result is a DPM result.

```objc
NSInteger isDPM
```

## isMirrored

This attribute stands for whether the barcode is mirrored.

```objc
NSInteger isMirrored
```
