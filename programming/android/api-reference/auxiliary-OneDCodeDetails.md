---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - OneDCodeDetails Class
description: This page shows the OneDCodeDetails Class of Dynamsoft Barcode Reader for Android SDK.
keywords: OneDCodeDetails, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---

# Class OneDCodeDetails

```java
import com.dynamsoft.dbr.OneDCodeDetails;
```

`OneDCodeDetails` is one of the [`detailedResult`](auxiliary-TextResult.md#detailedresult) in class `TextResult`. It stores the OneD code details.

| Attribute | Type |
|---------- |-----|
| `moduleSize` | *int* |
| `startCharsBytes` | *int* |
| `stopCharsBytes` | *int* |
| `checkDigitBytes` | *int* |
| `startPatternRange` | *int* |
| `middlePatternRange` | *int* |
| `endPatternRange` | *int* |

## moduleSize

The barcode module size (the minimum bar width in pixel).

```java
int com.dynamsoft.dbr.OneDCodeDetails.moduleSize
```

## startCharsBytes

The start chars in a byte array.

```java
byte[] com.dynamsoft.dbr.OneDCodeDetails.startCharsBytes
```

## stopCharsBytes

The stop chars in a byte array.

```java
byte[] com.dynamsoft.dbr.OneDCodeDetails.stopCharsBytes
```

## checkDigitBytes

The check digit chars in a byte array.

```java
byte[] com.dynamsoft.dbr.OneDCodeDetails.checkDigitBytes
```

## startPatternRange

The start pattern range of the OneDcode.

```java
byte[] com.dynamsoft.dbr.OneDCodeDetails.startPatternRange
```

## middlePatternRange

The middle pattern range of the OneDcode.

```java
byte[] com.dynamsoft.dbr.OneDCodeDetails.middlePatternRange
```

## endPatternRange

The end pattern range of the OneDcode.

```java
byte[] com.dynamsoft.dbr.OneDCodeDetails.endPatternRange
```
