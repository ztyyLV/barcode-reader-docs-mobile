---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Parameter and Runtime Settings Basic Methods
description: This page shows basic Runtime Settings methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: setModeArgument, getModeArgument, getRuntimeSettings, updateRuntimeSettings, resetRuntimeSettings, parameter and runtime settings basic methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
---

# Parameter and Runtime Settings Basic Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`getRuntimeSettings`](#getruntimesettings) | Get current runtime settings. |
  | [`updateRuntimeSettings (with Struct)`](#updateruntimesettings) | Update runtime settings with a given struct. |
  | [`updateRuntimeSettings (with preset template)`](#with-a-preset-template)) | Update runtime settings from one of the preset templates. |
  | [`resetRuntimeSettings`](#resetruntimesettings) | Resets all parameters to default values. |  
  | [`setModeArgument`](#setmodeargument) | Sets the optional argument for a specified mode in Modes parameters. |
  | [`getModeArgument`](#getmodeargument) | Gets the optional argument for a specified mode in Modes parameters. |

---

## getRuntimeSettings

Get current settings and save them into a [`iPublicRuntimeSettings`](auxiliary-iPublicRuntimeSettings.md) struct.

```objc
- (iPublicRuntimeSettings* _Nullable)getRuntimeSettings:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in, out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

A DBRPublicRuntimeSettings storing current runtime settings.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
NSError __autoreleasing * _Nullable error;
[barcodeReader getRuntimeSettings:&error];
```
2. 
```swift
let settings = try? barcodeReader.getRuntimeSettings()
```

## updateRuntimeSettings

### With a PublicRuntimeSettings Struct

Update runtime settings with a given [`iPublicRuntimeSettings`](auxiliary-iPublicRuntimeSettings.md) struct.

```objc
- (void)updateRuntimeSettings:(iPublicRuntimeSettings* _Nonnull)settings
                        error:(NSError* _Nullable * _Nullable)error
                        NS_SWIFT_NAME(updateRuntimeSettings(_:));
```

**Parameters**

`[in] settings` The struct of template settings.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
iPublicRuntimeSettings *settings = [barcodeReader getRuntimeSettings:nil];
// After you have made some changes on the runtime settings.
[barcodeReader updateRuntimeSettings:settings error:nil];
```
2. 
```swift
let settings = try? barcodeReader.getRuntimeSettings()
// After you have made some changes on the runtime settings.
try? barcodeReader.updateRuntimeSettings(settings!)
```

### With a Preset Template

```objc
- (void)updateRuntimeSettings:(EnumPresetTemplate)presetTemplate;
```

**Parameters**

`presetTemplate`: One of the preset templates.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader updateRuntimeSettings:EnumPresetTemplate.EnumPresetTemplateVideoSingleBarcode];
```
2. 
```swift
barcodeReader.updateRuntimeSettings(EnumPresetTemplate.EnumPresetTemplateVideoSingleBarcode)
```

## resetRuntimeSettings

Reset all parameters to default values.

```objc
- (void)resetRuntimeSettings:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader resetRuntimeSettings:nil];
```
2. 
```swift
try? barcodeReader.resetRuntimeSettings()
```

## setModeArgument

Sets the optional argument for a specified mode in Modes parameters.

```objc
-(void)setModeArgument:(NSString* _Nonnull)modeName
                    index:(NSInteger)index 
                    argumentName:(NSString* _Nonnull)argumentName
                    argumentValue:(NSString* _Nonnull)argumentValue
                    error:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in] modesName` The mode parameter name to set argument.  
`[in] index` The array index of mode parameter to indicate a specific mode.  
`[in] argumentName` The name of the argument to set.  
`[in] argumentValue` The value of the argument to set.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
iPublicRuntimeSettings *settings = [barcodeReader getRuntimeSettings:nil];
settings.binarizationModes = @[@(EnumBinarizationModeLocalBlock)];
[barcodeReader updateRuntimeSettings:settings error:nil];
[barcodeReader setModeArgument:@"BinarizationModes" index:0 argumentName:@"EnableFillBinaryVacancy" argumentValue:"1" error:nil];
```
2. 
```swift
let settings = try? barcodeReader.getRuntimeSettings()
settings!.binarizationModes = [EnumBinarizationMode.localBlock]
try? barcodeReader.updateRuntimeSettings(settings!)
try? barcodeReader.setModeArgument("BinarizationModes", index: 0, argumentName: "EnableFillBinaryVacancy", argumentValue: "1")
```

**Remarks**

Check follow link for available modes and arguments:

- [`BarcodeColourModes`]({{ site.parameters_reference }}image-parameter/BarcodeColourModes.html#barcodecolourmodes)
- [`BinarizationModes`]({{ site.parameters_reference }}image-parameter/BinarizationModes.html#binarizationmodes)
- [`ColourClusteringModes`]({{ site.parameters_reference }}image-parameter/ColourClusteringModes.html#colourclusteringmodes)
- [`ColourConversionModes`]({{ site.parameters_reference }}image-parameter/ColourConversionModes.html#colourconversionmodes)
- [`DeformationResistingModes`]({{ site.parameters_reference }}image-parameter/DeformationResistingModes.html#deformationresistingmodes)
- [`ImagePreprocessingModes`]({{ site.parameters_reference }}image-parameter/ImagePreprocessingModes.html#imagepreprocessingmodes)
- [`IntermediateResultSavingMode`]({{ site.parameters_reference }}image-parameter/IntermediateResultSavingMode.html#intermediateresultsavingmode)
- [`LocalizationModes`]({{ site.parameters_reference }}image-parameter/LocalizationModes.html#localizationmodes)
- [`RegionPredetectionModes`]({{ site.parameters_reference }}image-parameter/RegionPredetectionModes.html#regionpredetectionmodes)
- [`ScaleUpModes`]({{ site.parameters_reference }}image-parameter/ScaleUpModes.html#scaleupmodes)
- [`TextFilterModes`]({{ site.parameters_reference }}image-parameter/TextFilterModes.html#textfiltermodes)
- [`TextureDetectionModes`]({{ site.parameters_reference }}image-parameter/TextureDetectionModes.html#texturedetectionmodes)

## getModeArgument

Gets the optional argument for a specified mode in Modes parameters.

```objc
-(NSString* _Nonnull)getModeArgument:(NSString* _Nonnull)modeName
                               index:(NSInteger)index
                        argumentName:(NSString* _Nonnull)argumentName
                               error:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in] modesName` The mode parameter name to get arguments.  
`[in] index` The array index of mode parameter to indicate a specific mode.  
`[in] argumentName` The name of the argument to get.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

the optional argument for a specified mode

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
iPublicRuntimeSettings *settings = [barcodeReader getRuntimeSettings:nil];
settings.binarizationModes = @[@(EnumBinarizationModeLocalBlock)];
[barcodeReader updateRuntimeSettings:settings error:nil];
[barcodeReader setModeArgument:@"BinarizationModes" index:0 argumentName:@"EnableFillBinaryVacancy" argumentValue:"1" error:nil];
argumentValue = [barcodeReader getModeArgument:@"BinarizationModes" index:0 argumentName:@"EnableFillBinaryVacancy" error:&error];
```
2. 
```swift
let settings = try? barcodeReader.getRuntimeSettings()
settings?.binarizationModes![0] = EnumBinarizationMode.localBlock
try? barcodeReader.updateRuntimeSettings(settings!)
try? barcodeReader.setModeArgument("BinarizationModes", index: 0, argumentName: "EnableFillBinaryVacancy", argumentValue: "1")
let argumentValue = barcodeReader.getModeArgument("BinarizationModes", index: 0, argumentName: "EnableFillBinaryVacancy", error: &error)
```

**Remarks**

Check follow link for available modes and arguments:

- [`BarcodeColourModes`]({{ site.parameters_reference }}image-parameter/BarcodeColourModes.html#barcodecolourmodes)
- [`BinarizationModes`]({{ site.parameters_reference }}image-parameter/BinarizationModes.html#binarizationmodes)
- [`ColourClusteringModes`]({{ site.parameters_reference }}image-parameter/ColourClusteringModes.html#colourclusteringmodes)
- [`ColourConversionModes`]({{ site.parameters_reference }}image-parameter/ColourConversionModes.html#colourconversionmodes)
- [`DeformationResistingModes`]({{ site.parameters_reference }}image-parameter/DeformationResistingModes.html#deformationresistingmodes)
- [`ImagePreprocessingModes`]({{ site.parameters_reference }}image-parameter/ImagePreprocessingModes.html#imagepreprocessingmodes)
- [`IntermediateResultSavingMode`]({{ site.parameters_reference }}image-parameter/IntermediateResultSavingMode.html#intermediateresultsavingmode)
- [`LocalizationModes`]({{ site.parameters_reference }}image-parameter/LocalizationModes.html#localizationmodes)
- [`RegionPredetectionModes`]({{ site.parameters_reference }}image-parameter/RegionPredetectionModes.html#regionpredetectionmodes)
- [`ScaleUpModes`]({{ site.parameters_reference }}image-parameter/ScaleUpModes.html#scaleupmodes)
- [`TextFilterModes`]({{ site.parameters_reference }}image-parameter/TextFilterModes.html#textfiltermodes)
- [`TextureDetectionModes`]({{ site.parameters_reference }}image-parameter/TextureDetectionModes.html#texturedetectionmodes)
