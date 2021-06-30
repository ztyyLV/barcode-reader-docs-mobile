---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - OneDCodeDetails Class
description: This page shows the OneDCodeDetails Class of Dynamsoft Barcode Reader for Android SDK.
keywords: OneDCodeDetails, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---

# OneDCodeDetails

```java
import com.dynamsoft.dbr.OneDCodeDetails;
```

`OneDCodeDetails` is one of the [`detailedResult`](class-TextResult.md#detailedresult) in class `TextResult`. It stores the OneD code details.

## Attributes
  
| Attribute | Type |
|---------- | ---- |
| [`moduleSize`](#modulesize) | The barcode module size (the minimum bar width in pixel). |
| [`startCharsBytes`](#startcharsbytes) | The start chars in a byte array. |
| [`stopCharsBytes`](#stopcharsbytes) | The stop chars in a byte array. |
| [`checkDigitBytes`](#checkdigitbytes) | The check digit chars in a byte array. |
| [`startPatternRange`](#startpatternrange) | The start pattern range of the OneDcode. |
| [`middlePatternRange`](#middlepatternrange) | The middle pattern range of the OneDcode. |
| [`endPatternRange`](#endpatternrange) | The end pattern range of the OneDcode. |

## Usage

```java
//The textresult[i] is one of the text result you got  
OneDCodeDetails oneDDetails = (OneDCodeDetails) textresult[i].detailedResult;
int oneD_moduleSize = oneDDetails.moduleSize;
int oneD_startCharsBytes = oneDDetails.startCharsBytes;
int oneD_stopCharsBytes = oneDDetails.stopCharsBytes;
int oneD_checkDigitBytes = oneDDetails.checkDigitBytes;
int oneD_startPatternRange = oneDDetails.startPatternRange;
int oneD_middlePatternRange = oneDDetails.middlePatternRange;
int oneD_endPatternRange = oneDDetails.endPatternRange;
```
