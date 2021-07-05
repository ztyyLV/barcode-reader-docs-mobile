---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - DCESettingParameters Class
description: This page shows the DCESettingParameters Class of Dynamsoft Barcode Reader for Android SDK.
keywords: DCESettingParameters, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---

# Class DCESettingParameters

```java
import com.dynamsoft.dbr.DCESettingParameters;
```

Stores the DCESettingParameters information.

| Attribute | type |
|-----------|------|
| `cameraInstance` | *Object* |
|  `textResultCallback` | [`TextResultCallback`]({{site.android_api}}interface.html#textresultcallback) |
| `textResultCallback_UserData` | *Object*  |
| `intermediateResultCallback` | [`IntermediateResultCallback`]({{site.android_api}}interface.html#intermediateresultcallback) |
| `IntermediateResultCallback_UserData` | *Object* |

## CameraInstance

The Camera Enhancer instance.

```java
settingParameters.cameraInstance = mCameraEnhancer;
```

## textResultCallback

Set text result callback.

```java
settingParameters.textResultCallback =mTextResultCallback;
```

The `TextResultCallback` includes the following Parameters:

- `frameID`: The ID of frame.
- `results`: The recognized barcode result of the frame.
- `userData`: Arguments passed to your function.

## textResultCallback_UserData

Set the `UserData` of the `TextResultCallback`.

```java
settingParameters.textResultCallback_UserData =userData;
```

## intermediateResultCallback

Set intermediate result call back.

```java
settingParameters.intermediateResultCallback = mIntermediateResultCallback;
```

The `IntermediateResultCallback` includes the following Parameters:

- `frameID`: The ID of frame.
- `results`: The intermediate result of the frame.
- `userData`: Arguments passed to your function.

## intermediateResultCallback_UserData

Set the `UserData` of the `IntermediateResultCallback`.

```java
settingParameters.intermediateResultCallback_UserData =userData;
```
