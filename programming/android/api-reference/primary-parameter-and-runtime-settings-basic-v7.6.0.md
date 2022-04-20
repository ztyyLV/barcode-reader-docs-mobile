---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReader Parameter and Runtime Settings Basic Methods
description: This page shows BarcodeReader basic runtime settings methods of Dynamsoft Barcode Reader for Android SDK.
keywords: setModeArgument, getModeArgument, getRuntimeSettings, updateRuntimeSettings, resetRuntimeSettings, parameter and runtime settings basic methods, BarcodeReader, api reference, android
needAutoGenerateSidebar: true
---


# Android API Reference - BarcodeReader Parameter and Runtime Settings Basic Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`getRuntimeSettings`](#getruntimesettings) | Get current runtime settings. |
  | [`updateRuntimeSettings`](#updateruntimesettings) | Modify and update the current runtime settings. |
  | [`resetRuntimeSettings`](#resetruntimesettings) | Reset runtime settings to default. |

  ---

## getRuntimeSettings

Get current settings and save them into a [`PublicRuntimeSettings`](../class/PublicRuntimeSettings.md) struct.

```java
PublicRuntimeSettings com.dynamsoft.barcode.BarcodeReader.getRuntimeSettings() throws BarcodeReaderException
```

**Return value**

The struct of template settings.

**Exceptions**

[`BarcodeReaderException`](../class/BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
PublicRuntimeSettings settings = reader.getRuntimeSettings();
```

## updateRuntimeSettings

Update runtime settings with a given [`PublicRuntimeSettings`](../class/PublicRuntimeSettings.md) struct.

```java
void com.dynamsoft.barcode.BarcodeReader.updateRuntimeSettings(PublicRuntimeSettings settings) throws BarcodeReaderException
```

**Parameters**

`settings`: The struct of template settings.

**Exceptions**

[`BarcodeReaderException`](../class/BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.deblurLevel = 9;
reader.updateRuntimeSettings(settings);
```

## resetRuntimeSettings

Reset all parameters to default values.

```java
void com.dynamsoft.barcode.BarcodeReader.resetRuntimeSettings() throws BarcodeReaderException
```

**Exceptions**
[`BarcodeReaderException`](../class/BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.deblurLevel = 9;
reader.updateRuntimeSettings(settings);
reader.resetRuntimeSettings();
```
