---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - DCESettingParameters Class
description: This page shows the DCESettingParameters Class of Dynamsoft Barcode Reader for Android SDK.
keywords: DCESettingParameters, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---

# DCESettingParameters

Stores the DCESettingParameters information.

## Attributes

| Attribute | type |
|-----------|------|
| [`CameraInstance`](#camerainstance) | *Object* |
| [`textResultCallback`](#textresultcallback) | [`TextResultCallback`]({{site.android_api}}interface.html#textresultcallback) |
| [`textResultCallback_UserData`](#textresultcallback_userdata) | *Object* |
| [`irtCallback`](#irtcallback) | [`IntermediateResultCallback`]({{site.android_api}}interface.html#intermediateresultcallback) |
| [`irtCallback_UserData`](#irtcallback_userdata) | *Object* |

### CameraInstance

```java
    Object com.dynamsoft.dbr.DCESettingParameters.CameraInstance
```

### textResultCallback

Set text result callback.

```java
    TextResultCallback com.dynamsoft.dbr.DCESettingParameters.textResultCallback
```

The `TextResultCallback` includes the following Parameters:

- `frame`: The frame data.
- `frameID`: The ID of frame.
- `results`: The recognized barcode result of the frame.
- `userData`: Arguments passed to your function.

### textResultCallback_UserData

Set the `UserData` of the `TextResultCallback`.

```java
    Object com.dynamsoft.dbr.DCESettingParameters.textResultCallback_UserData
```

### irtCallback

Set intermediate result call back.

```java
    IntermediateResultCallback com.dynamsoft.dbr.DCESettingParameters.irtCallback
```

The `IntermediateResultCallback` includes the following Parameters:

- `frameID`: The ID of frame.
- `results`: The intermediate result of the frame.
- `userData`: Arguments passed to your function.

### irtCallback_UserData

Set the `UserData` of the `IntermediateResultCallback`.

```java
    Object com.dynamsoft.dbr.DCESettingParameters.irtCallback_UserData
```
