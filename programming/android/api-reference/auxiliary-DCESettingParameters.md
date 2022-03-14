---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - DCESettingParameters Class
description: This page shows the DCESettingParameters Class of Dynamsoft Barcode Reader for Android SDK.
keywords: DCESettingParameters, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
pageStartVer: 8.6
---

# DCESettingParameters

> Note:  
> This class is removed in 9.0 version. Please use the [video methods](primary-video.md) for video barcode scanning if you are using the latest version.

Stores the DCESettingParameters information. The parameters controls the video streaming barcode decoding.

```java
class com.dynamsoft.dbr.DCESettingParameters;
```

| Attribute | type | Descriptions |
|-----------|------|-------------|
| [`cameraInstance`](#camerainstance) | *Object* | The Camera Enhancer instance |
| [`textResultCallback`](#textresultcallback) | [`TextResultCallback`]({{site.android_api}}interface.html#textresultcallback) | Set text result callback. |
| [`textResultCallback_UserData`](#textresultcallback_userdata) | *Object*  | Transfer user data. |
| [`intermediateResultCallback`](#intermediateresultcallback) | [`IntermediateResultCallback`]({{site.android_api}}interface.html#intermediateresultcallback) | Set intermediate result callback. |
| [`IntermediateResultCallback_UserData`](#intermediateresultcallback_userdata) | *Object* | Transfer user data. |

## cameraInstance

The Camera Enhancer instance.

```java
settingParameters.cameraInstance = mCameraEnhancer;
```

## textResultCallback

Set text result callback.

```java
settingParameters.textResultCallback =mTextResultCallback;
```

**Parameters**

`frameID`: The ID of frame.  
`results`: The recognized barcode result of the frame.  
`userData`: Arguments passed to your function.

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

**Parameters**

`frameID`: The ID of frame.  
`results`: The intermediate result of the frame.  
`userData`: Arguments passed to your function.

## intermediateResultCallback_UserData

Set the `UserData` of the `IntermediateResultCallback`.

```java
settingParameters.intermediateResultCallback_UserData =userData;
```
