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
  | [`setModeArgument`](#setmodeargument) | Set argument value for the specified mode parameter. |
  | [`getModeArgument`](#getmodeargument) | Get argument value for the specified mode parameter. |
  | [`getRuntimeSettings`](#getruntimesettings) | Get current runtime settings. |
  | [`updateRuntimeSettings`](#updateruntimesettings) | Modify and update the current runtime settings. |
  | [`resetRuntimeSettings`](#resetruntimesettings) | Reset runtime settings to default. |

  ---

## setModeArgument

Sets the optional argument for a specified mode in Modes parameters.

```java
void setModeArgument(String modesName, int index, String argumentName, String argumentValue) throws BarcodeReaderException
```

**Parameters**

`modesName`: The mode parameter name to set argument.  
`index`: The array index of mode parameter to indicate a specific mode.  
`argumentName`: The name of the argument to set.  
`argumentValue`: The value of the argument to set.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.binarizationModes[0] = EnumBinarizationMode.BM_LOCAL_BLOCK;
reader.updateRuntimeSettings(settings);
reader.setModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy", "1");
reader.destroy();
```

**Remarks**

Check the available modes and arguments below:

- [`BarcodeColourModes`]({{ site.parameters_reference }}barcode-colour-modes.html)
- [`BinarizationModes`]({{ site.parameters_reference }}binarization-modes.html)
- [`ColourClusteringModes`]({{ site.parameters_reference }}colour-clustering-modes.html)
- [`ColourConversionModes`]({{ site.parameters_reference }}colour-conversion-modes.html)
- [`DeformationResistingModes`]({{ site.parameters_reference }}deformation-resisting-modes.html)
- [`ImagePreprocessingModes`]({{ site.parameters_reference }}image-preprocessing-modes.html)
- [`IntermediateResultSavingMode`]({{ site.parameters_reference }}intermediate-result-saving-mode.html)
- [`LocalizationModes`]({{ site.parameters_reference }}localization-modes.html)
- [`RegionPredetectionModes`]({{ site.parameters_reference }}region-predetection-modes.html)
- [`ScaleUpModes`]({{ site.parameters_reference }}scale-up-modes.html)
- [`TextFilterModes`]({{ site.parameters_reference }}text-filter-modes.html)
- [`TextureDetectionModes`]({{ site.parameters_reference }}texture-detection-modes.html)

## getModeArgument

Gets the optional argument for a specified mode in Modes parameters.

```java
String getModeArgument(String modesName, int index, String argumentName) throws BarcodeReaderException
```

**Parameters**

`modesName`: The mode parameter name to get argument.  
`index`: The array index of mode parameter to indicate a specific mode.  
`argumentName`: The name of the argument to get.

**Return Value**

the optional argument for a specified mode in Modes parameters.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.binarizationModes[0] = EnumBinarizationMode.BM_LOCAL_BLOCK;
reader.updateRuntimeSettings(settings);
reader.setModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy", "1");
String argumentValue = reader.getModeArgument("BinarizationModes", 0, "EnableFillBinaryVacancy");
reader.destroy();
```

**Remarks**

Check the available modes and arguments below:

- [`BarcodeColourModes`]({{ site.parameters_reference }}barcode-colour-modes.html)
- [`BinarizationModes`]({{ site.parameters_reference }}binarization-modes.html)
- [`ColourClusteringModes`]({{ site.parameters_reference }}colour-clustering-modes.html)
- [`ColourConversionModes`]({{ site.parameters_reference }}colour-conversion-modes.html)
- [`DeformationResistingModes`]({{ site.parameters_reference }}deformation-resisting-modes.html)
- [`ImagePreprocessingModes`]({{ site.parameters_reference }}image-preprocessing-modes.html)
- [`IntermediateResultSavingMode`]({{ site.parameters_reference }}intermediate-result-saving-mode.html)
- [`LocalizationModes`]({{ site.parameters_reference }}localization-modes.html)
- [`RegionPredetectionModes`]({{ site.parameters_reference }}region-predetection-modes.html)
- [`ScaleUpModes`]({{ site.parameters_reference }}scale-up-modes.html)
- [`TextFilterModes`]({{ site.parameters_reference }}text-filter-modes.html)
- [`TextureDetectionModes`]({{ site.parameters_reference }}texture-detection-modes.html)

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
