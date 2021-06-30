---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - DCESettingParameters Class
description: This page shows the DCESettingParameters Class of Dynamsoft Barcode Reader for Android SDK.
keywords: DCESettingParameters, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---

# DCESettingParameters

```java
import com.dynamsoft.dbr.DCESettingParameters;
```

Stores the DCESettingParameters information.

## Attributes

| Attribute | type | Description |
|-----------|------|-------------|
| `cameraInstance` | *Object* | The Camera Enhancer instance |
|  `textResultCallback` | [`TextResultCallback`]({{site.android_api}}interface.html#textresultcallback) | Set text result callback. |
| `textResultCallback_UserData` | *Object*  | Transfer user data. |
| `intermediateResultCallback` | [`IntermediateResultCallback`]({{site.android_api}}interface.html#intermediateresultcallback) | Set intermediate result callback. |
| `IntermediateResultCallback_UserData` | *Object* | Transfer user data. |

## Usage

```java
DCESettingParameters settingParameters = new DCESettingParameters();
settingParameters.cameraInstance = mCameraEnhancer;
settingParameters.textResultCallback =mTextResultCallback;
settingParameters.intermediateResultCallback = mIntermediateResultCallback;
barcodeReader.SetCameraEnhancerParam(settingParameters);
```
