---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReader initialization and Destroy
description: This page shows BarcodeReader initialization and Destroy methods of Dynamsoft Barcode Reader for Android SDK.
keywords: destroy, BarcodeReader, initialization and destroy, api reference, android
needAutoGenerateSidebar: true
noTitleIndex: true
---

# Initialization and Destroy Methods

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
