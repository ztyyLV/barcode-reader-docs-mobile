---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Parameter and Runtime Settings Advanced Methods
description: This page shows advanced Runtime Settings methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: initRuntimeSettingsWithFile, initRuntimeSettingsWithString, appendTplFileToRuntimeSettings, appendTplStringToRuntimeSettings, allParameterTemplateNames, outputSettingsToFile, outputSettingsToString, parameter and runtime settings advanced methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
---

# Parameter and Runtime Settings Advanced Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`initRuntimeSettingsWithFile`](#initruntimesettingswithfile) | Initialize runtime settings with the settings in a given JSON file. |
  | [`initRuntimeSettingsWithString`](#initruntimesettingswithstring) | Initialize runtime settings with the settings in a given JSON string. |
  | [`appendTplFileToRuntimeSettings`](#appendtplfiletoruntimesettings) | Append a new template file to the current runtime settings. |
  | [`appendTplStringToRuntimeSettings`](#appendtplstringtoruntimesettings) | Append a new template string to the current runtime settings. |
  | [`allParameterTemplateNames`](#allparametertemplatenames) | Gets the parameter templates name array. |
  | [`outputSettingsToFile`](#outputsettingstofile) | Output runtime settings to a settings file (JSON file). |
  | [`outputSettingsToString`](#outputsettingstostring) | Output runtime settings to a string. |

---

## initRuntimeSettingsWithFile

Initialize runtime settings with the parameters obtained from a JSON file.

```objc
- (void)initRuntimeSettingsWithFile:(NSString* _Nonnull)fileName
                       conflictMode:(EnumConflictMode)conflictMode
                              error:(NSError* _Nullable * _Nullable)error
                              NS_SWIFT_NAME(initRuntimeSettingsWithFile(_:conflictMode:));
```

**Parameters**

`[in] fileName` The settings file path.  
`[in] conflictMode` The parameter setting mode, which decides whether to inherit parameters from previous template settings or to overwrite previous settings with the new template.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.  

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader initRuntimeSettingsWithFile:@"your template file path" conflictMode:EnumConflictModeOverwrite error:nil];
```
2. 
```swift
try? barcodeReader.initRuntimeSettingsWithFile("your template file path", conflictMode:EnumConflictMode.overwrite)
```

## initRuntimeSettingsWithString

Initialize runtime settings with the parameters obtained from a JSON string.

```objc
- (void)initRuntimeSettingsWithString:(NSString* _Nonnull)content
                         conflictMode:(EnumConflictMode)conflictMode
                                error:(NSError* _Nullable * _Nullable)error
                                NS_SWIFT_NAME(initRuntimeSettingsWithString(_:conflictMode:));
```

**Parameters**

`[in] content` A JSON string that represents the content of the settings.  
`[in] conflictMode` The parameter setting mode, which decides whether to inherit parameters from previous template setting or to overwrite previous settings with the new template.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader initRuntimeSettingsWithString:@"{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}" conflictMode:EnumConflictModeOverwrite error:nil];
```
2. 
```swift
try? barcodeReader.initRuntimeSettingsWithString(content:"{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}", conflictMode:EnumConflictMode.overwrite)
```

## appendTplFileToRuntimeSettings

Append a new template file to the current runtime settings.

```objc
- (void)appendTplFileToRuntimeSettings:(NSString * _Nonnull)fileName
                          conflictMode:(EnumConflictMode)conflictMode
                                 error:(NSError * _Nullable *_Nullable)error
                                 NS_SWIFT_NAME(appendTplFileToRuntimeSettings(_:conflictMode:));
```

**Parameters**

`[in] fileName` The settings file path.  
`[in] conflictMode` The parameter setting mode, which decides whether to inherit parameters from previous template settings or to overwrite previous settings with the new template.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader appendTplFileToRuntimeSettings:@"your template file path" conflictMode:EnumConflictModeIgnore error:nil];
```
2. 
```swift
try? barcodeReader.appendTplFileToRuntimeSettings(fileName:"your template file path", conflictMode:EnumConflictMode.ignore, error:&error)
```

## appendTplStringToRuntimeSettings

Append a new template string to the current runtime settings.

```objc
- (void)appendTplStringToRuntimeSettings:(NSString * _Nonnull)content
                            conflictMode:(EnumConflictMode)conflictMode
                                   error:(NSError *_Nullable *_Nullable)error   
                                   NS_SWIFT_NAME(appendTplStringToRuntimeSettings(_:conflictMode:));
```

**Parameters**

`[in] content` A JSON string that represents the content of the settings.  
`[in] conflictMode` The parameter setting mode, which decides whether to inherit parameters from previous template setting or to overwrite previous settings with the new template.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader initRuntimeSettingsWithString:@"{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}" conflictMode:EnumConflictModeOverwrite error:nil];
[barcodeReader appendTplStringToRuntimeSettings:@"{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_OneD\"], \"ExpectedBarcodesCount\":20}}" conflictMode:EnumConflictModeIgnore error:nil];
```
2. 
```swift
try? barcodeReader.initRuntimeSettingsWithString(content:"{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_QR_CODE\"], \"ExpectedBarcodesCount\":10}}", conflictMode:EnumConflictMode.Overwrite)
try? barcodeReader.appendTplStringToRuntimeSettings(content:"{\"Version\":\"3.0\", \"ImageParameter\":{\"Name\":\"IP1\", \"BarcodeFormatIds\":[\"BF_OneD\"], \"ExpectedBarcodesCount\":20}}", conflictMode:EnumConflictMode.ignore)
```

## allParameterTemplateNames

Get count of parameter templates.

```objc
- (NSArray<NSString*>* _Nullable)allParameterTemplateNames: (NSError *__autoreleasing  _Nullable * _Nullable)error;
```

**Parameters**

`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

The template name array.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
NSArray* allTplNames = [barcodeReader allParameterTemplateNames:nil];
```
2. 
```swift
let allTplNames = try? barcodeReader.allParameterTemplateNames()
```

## outputSettingsToFile

Outputs runtime settings and save them into a settings file (JSON file).  

```objc
- (void)outputSettingsToFile:(NSString *_Nullable)filePath 
                settingsName:(NSString*_Nonnull)settingsName 
                       error:(NSError*_Nullable *_Nullable)error   
                       NS_SWIFT_NAME(outputSettingsToFile(_:settingsName:));
```

**Parameters**

`[in] filePath` The path of the output file which stores current settings.  
`[in] settingsName` A unique name for declaring current runtime settings.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
settingsName = [barcodeReader outputSettingsToFile:@"your saving file path" settingsName:@"currentRuntimeSettings" error:nil];
```
2. 
```swift
let settingsName = try? barcodeReader.outputSettingsToFile("your saving file path", settingsName:"currentRuntimeSettings")
```

## outputSettingsToString

Output runtime settings to a string.

```objc
- (NSString *_Nullable)outputSettingsToString:(NSString*_Nonnull)settingsName 
                                        error:(NSError* _Nullable * _Nullable)error  
                                        NS_SWIFT_NAME(outputSettingsToString(_:));
```

**Parameters**

`[in] settingsName` A unique name for declaring current runtime settings.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

The output string which stores the content of current settings.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
settingsName = [barcodeReader outputSettingsToString:@"currentRuntimeSettings" error:nil];
```
2. 
```swift
let settingsName = try? barcodeReader.outputSettingsToString("currentRuntimeSettings")
```
