---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReader initialization
description: This page shows BarcodeReader initialization methods of Dynamsoft Barcode Reader for Android SDK.
keywords: BarcodeReader, initialization, api reference, android
needAutoGenerateSidebar: true
---

# Android API Reference - BarcodeReader Initialization

  | Method               | Description |
  |----------------------|-------------|
  | [`BarcodeReader`](#barcodereader) | Initialization of `BarcodeReader` object.|

---

## BarcodeReader Initialization

Initialization of `BarcodeReader` object without a license.

```java
com.dynamsoft.barcode.BarcodeReader.BarcodeReader() throws BarcodeReaderException
```

Initialization of `BarcodeReader` with a license.

```java
com.dynamsoft.barcode.BarcodeReader.BarcodeReader(String license)	throws Exception
```

**Exceptions**

[`BarcodeReaderException`](../class/BarcodeReaderException.md)

**Remark**s

If you initialize DynamsoftBarcodeReader without a license, the decoding results may be unreliable.

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
```

```java
BarcodeReader reader = new BarcodeReade("t0260NwAAAHV***************");
```
