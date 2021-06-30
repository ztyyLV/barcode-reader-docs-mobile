---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - AztecDetails Class
description: This page shows the AztecDetails Class of Dynamsoft Barcode Reader for Android SDK.
keywords: AztecDetails, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---


# Class AztecDetails

`AztecDetails` is an extension of the class `textResult`. It stores the Aztec code details.

## Attributes
  
| Attribute | Description |
|---------- | ----------- |
| `int moduleSize;`| The barcode module size (the minimum bar width in pixel). |
| `int rows;` | The row count of the barcode. |
| `int columns;` | The column count of the barcode. |
| `int layerNumber;` | A negative number (-1, -2, -3, -4) specifies a compact Aztec code. A positive number (1, 2, .. 32) specifies a normal (full-rang) Aztec code. |

## Usage

```java
import com.dynamsoft.dbr.AztecDetails;
```

```java
//The textresult[i] is one of the text result you got  
AztecDetails aztecDetails = (AztecDetails) textresult[i].detailedResult;
int aztec_moduleSize = aztecDetails.moduleSize;
int aztec_columns = aztecDetails.columns;
int aztec_rows = aztecDetails.rows;
int aztec_layerNumber = aztecDetails.layerNumber;
```
