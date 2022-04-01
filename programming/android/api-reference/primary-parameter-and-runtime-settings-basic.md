---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReader Parameter and Runtime Settings Basic Methods
description: This page shows BarcodeReader basic runtime settings methods of Dynamsoft Barcode Reader for Android SDK.
keywords: setModeArgument, getModeArgument, getRuntimeSettings, updateRuntimeSettings, resetRuntimeSettings, parameter and runtime settings basic methods, BarcodeReader, api reference, android
needAutoGenerateSidebar: true
noTitleIndex: true
---


# Parameter and Runtime Settings Basic Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`getRuntimeSettings`](#getruntimesettings) | Get current runtime settings. |
  | [`updateRuntimeSettings (with struct)`](#updateruntimesettings) | Modify and update the current runtime settings. |
  | [`updateRuntimeSettings (with preset template)`](#with-a-preset-template) | Update runtime settings from one of the preset templates. |
  | [`resetRuntimeSettings`](#resetruntimesettings) | Reset runtime settings to default. |

  ---

## getRuntimeSettings

Get current settings and save them into a [`PublicRuntimeSettings`](auxiliary-PublicRuntimeSettings.md) struct.

```java
PublicRuntimeSettings getRuntimeSettings() throws BarcodeReaderException
```

**Return Value**

The struct of template settings.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
PublicRuntimeSettings settings = reader.getRuntimeSettings();
reader.destroy();
```

## updateRuntimeSettings

### With a PublicRuntimeSettings Struct

Update runtime settings with a given [`PublicRuntimeSettings`](auxiliary-PublicRuntimeSettings.md) struct.

```java
void updateRuntimeSettings(PublicRuntimeSettings settings) throws BarcodeReaderException
```

**Parameters**

`settings`: The struct of template settings.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.deblurLevel = 9;
reader.updateRuntimeSettings(settings);
reader.destroy();
```

### With a Preset Template

Update the runtime settings from one of the preset templates.

```java
void updateRuntimeSettings(EnumPresetTemplate presetTemplate)
```

**Parameters**

`presetTemplate`: One of the preset templates.

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
reader.updateRuntimeSettings(EnumPresetTemplate.VIDEO_SINGLE_BARCODE);
reader.destroy();
```

## resetRuntimeSettings

Reset all parameters to default values.

```java
void resetRuntimeSettings() throws BarcodeReaderException
```

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.deblurLevel = 9;
reader.updateRuntimeSettings(settings);
reader.resetRuntimeSettings();
reader.destroy();
```
