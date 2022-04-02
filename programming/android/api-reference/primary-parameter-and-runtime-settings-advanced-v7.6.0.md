---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReader Parameter and Runtime Settings Advanced Methods
description: This page shows BarcodeReader advanced runtime settings methods of Dynamsoft Barcode Reader for Android SDK.
keywords: initRuntimeSettingsWithFile, initRuntimeSettingsWithString, appendTplFileToRuntimeSettings, appendTplStringToRuntimeSettings, getAllParameterTemplateNames, outputSettingsToFile, outputSettingsToString, parameter and runtime settings advanced methods, BarcodeReader, api reference, android
needAutoGenerateSidebar: true
---

# Android API Reference - BarcodeReader Parameter and Runtime Settings Advanced Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`initRuntimeSettingsWithFile`](#initruntimesettingswithfile)  | Initialize runtime settings with the settings in a given JSON file. |
  | [`initRuntimeSettingsWithString`](#initruntimesettingswithstring) | Initialize runtime settings with the settings in a given JSON string. |
  | [`appendTplFileToRuntimeSettings`](#appendtplfiletoruntimesettings) | Append a new template file to the current runtime settings. |
  | [`appendTplStringToRuntimeSettings`](#appendtplstringtoruntimesettings) | Append a new template string to the current runtime settings. |
  | [`getAllParameterTemplateNames`](#getallparametertemplatenames) | Gets the parameter templates name array. |
  | [`outputSettingsToFile`](#outputsettingstofile) | Output runtime settings to a settings file (JSON file). |
  | [`outputSettingsToString`](#outputsettingstostring) | Output runtime settings to a string. |
  | [`setModeArgument`](#setmodeargument) | Set argument value for the specified mode parameter. |
  | [`getModeArgument`](#getmodeargument) | Get argument value for the specified mode parameter. |

  ---

## initRuntimeSettingsWithFile

Initialize runtime settings with the settings in a given JSON file.

```java
void com.dynamsoft.barcode.BarcodeReader.initRuntimeSettingsWithFile(String filePath, int enumConflictMode) throws BarcodeReaderException
```

**Parameters**

`filePath`: The path of the settings file.  
`enumConflictMode`: The parameter setting mode, which decides whether to inherit parameters from previous template setting or to overwrite previous settings and replace with the new template.

**Exceptions**

[`BarcodeReaderException`](../class/BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
reader.initRuntimeSettingsWithFile("your template file path", EnumConflictMode.CM_OVERWRITE);
reader.destroy();
```

## initRuntimeSettingsWithString

Initialize runtime settings with the settings in a given JSON string.

```java
void com.dynamsoft.barcode.BarcodeReader.initRuntimeSettingsWithString(String content, int enumConflictMode)throws BarcodeReaderException
```

**Parameters**

`content`: A JSON string that represents the content of the settings.  
`enumConflictMode`: The parameter setting mode, which decides whether to inherit parameters from previous template setting or to overwrite previous settings and replace with the new template.

**Exceptions**

[`BarcodeReaderException`](../class/BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
reader.initRuntimeSettingsWithString("{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}", EnumConflictMode.CM_OVERWRITE);
reader.destroy();
```

## appendTplFileToRuntimeSettings

Append a new template file to the current runtime settings.

```java
void com.dynamsoft.barcode.BarcodeReader.appendTplFileToRuntimeSettings(String filePath, int enumConflictMode) throws BarcodeReaderException
```

**Parameters**

`filePath`: The path of the settings file.  
`enumConflictMode`: The parameter setting mode, which decides whether to inherit parameters from previous template setting or to overwrite previous settings with the new template.

**Exceptions**

[`BarcodeReaderException`](../class/BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
reader.appendTplFileToRuntimeSettings("your template file path", EnumConflictMode.CM_IGNORE);
reader.destroy();
```

## appendTplStringToRuntimeSettings

Append a new template string to the current runtime settings.

```java
void com.dynamsoft.barcode.BarcodeReader.appendTplStringToRuntimeSettings(String content, int enumConflictMode)	throws BarcodeReaderException	
```

**Parameters**

`content`: A JSON string that represents the content of the settings.  
`enumConflictMode`: The parameter setting mode, which decides whether to inherit parameters from previous template setting or to overwrite previous settings with the new template.  

**Exceptions**

[`BarcodeReaderException`](../class/BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
reader.initRuntimeSettingsWithString("{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}", EnumConflictMode.CM_OVERWRITE);
reader.appendTplStringToRuntimeSettings("{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_OneD\"], \"ExpectedBarcodesCount\":20}}", EnumConflictMode.CM_IGNORE);
reader.destroy();
```

## getAllParameterTemplateNames

Gets the parameter templates name array.

```java
String [] com.dynamsoft.barcode.BarcodeReader.getAllParameterTemplateNames()
```

**Return value**

The template name array.

**Exceptions**

[`BarcodeReaderException`](../class/BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
String[] templateNames = reader.getAllParameterTemplateNames();
reader.destroy();
```

## outputSettingsToFile

Output runtime settings to a settings file (JSON file).

```java
void com.dynamsoft.barcode.BarcodeReader.outputSettingsToFile(String filePath, String settingsName) throws BarcodeReaderException
```

**Parameters**

`filePath`: The output file path which stores current settings.  
`settingsName`: A unique name for declaring current runtime settings.

**Exceptions**

[`BarcodeReaderException`](../class/BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
reader.outputSettingsToFile("your saving file path", "currentRuntimeSettings");
reader.destroy();
```

## outputSettingsToString

Output runtime settings to a string.

```java
String com.dynamsoft.barcode.BarcodeReader.outputSettingsToString(String settingsName) throws BarcodeReaderException
```

**Parameters** 

`settingsName` A unique name for declaring current runtime settings.  

**Return value**

The output string which stores the contents of current settings.

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader("t0260NwAAAHV***************");
String settingStr = reader.outputSettingsToString("currentRuntimeSettings");
reader.destroy();
```

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
