---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReader initialization
description: This page shows BarcodeReader initialization methods of Dynamsoft Barcode Reader for Android SDK.
keywords: BarcodeReader, initialization, api reference, android
needAutoGenerateSidebar: true
noTitleIndex: true
---

# initialization methods

  | Method               | Description |
  |----------------------|-------------|
  | [`BarcodeReader`](#barcodereader-initialization) | Initialization of `BarcodeReader` object.|

---

## BarcodeReader Initialization

Initialization of `BarcodeReader` object without a license.

```java
BarcodeReader() throws BarcodeReaderException
```

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader;
reader = new BarcodeReader();
```

**Remarks**

`BarcodeReader(String license)` is deprecated and will be removed in the future. Please use `BarcodeReader()` instead.
