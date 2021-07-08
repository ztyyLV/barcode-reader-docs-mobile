---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Methods
description: This page shows all methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
breadcrumbText: Methods
---

# BarcodeReader Class

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ## [Initialize and Destroy](primary-initialize.md)
> <hr>
> * [init](primary-initialize.md)
>
> ## [Decode](primary-decode.md)
> <hr>
> * [decodeFileWithName](primary-decode.md#decodefilewithname)
> * [decodeImage](primary-decode.md#decodeimage)
> * [decodeBuffer](primary-decode.md#decodebuffer)
> * [decodeBase64](primary-decode.md#decodebase64)
> * [createIntermediateResult](primary-decode.md#createintermediateresult)
> * [decodeIntermediateResults](primary-decode.md#decodeintermediateresults)
>
> ## [Camera Enhancer](primary-camera.md)
> <hr>
> * [SetCameraEnhancerParam](primary-camera.md#setcameraenhancerparam)
>
> ## [License](primary-license.md)
> <hr>
> * [initWithLicense](primary-license.md#initwithlicense)
> * [initWithLicenseFromServer](primary-license.md#initwithlicensefromserver)
> * [outputLicenseToString](primary-license.md#outputlicensetostring)
> * [initLicenseFromDLS](primary-license.md#initLicenseFromDLS)
>
> ## Parameter and Runtime Settings
>
> ### [Basic](primary-parameter-and-runtime-settings-basic.md)
> <hr>
> * [setModeArgument](primary-parameter-and-runtime-settings-basic.md#setmodeargument)
> * [getModeArgument](primary-parameter-and-runtime-settings-basic.md#getmodeargument)
> * [getRuntimeSettings](primary-parameter-and-runtime-settings-basic.md#getruntimesettings)
> * [updateRuntimeSettings](primary-parameter-and-runtime-settings-basic.md#updateruntimesettings)
> * [resetRuntimeSettings](primary-parameter-and-runtime-settings-basic.md#resetruntimesettings)
>
> ### [Advanced](primary-parameter-and-runtime-settings-advanced.md)
> <hr>
> * [initRuntimeSettingsWithFile](primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithfile)
> * [initRuntimeSettingsWithString](primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithstring)
> * [appendTplFileToRuntimeSettings](primary-parameter-and-runtime-settings-advanced.md#appendtplfiletoruntimesettings)
> * [appendTplStringToRuntimeSettings](primary-parameter-and-runtime-settings-advanced.md#appendtplstringtoruntimesettings)
> * [allparametertemplatenames](primary-parameter-and-runtime-settings-advanced.md#allparametertemplatenames)
> * [outputSettingsToFile](primary-parameter-and-runtime-settings-advanced.md#outputsettingstofile)
> * [outputSettingsToString](primary-parameter-and-runtime-settings-advanced.md#outputsettingstostring)
>
> ## [Result](primary-result.md)
> <hr>
> * [getIntermediateResults](primary-result.md#getintermediateresults)
>
> ## [Video](primary-video.md)
>
> ### Decode
> <hr>
> * [startFrameDecoding](primary-video.md#startframedecoding)
> * [startFrameDecodingEx](primary-video.md#startframedecodingex)
> * [appendFrame](primary-video.md#appendframe)
> * [stopFrameDecoding](primary-video.md#stopframedecoding)
>
> ### Parameter
> <hr>
> * [getFrameDecodingParameters](primary-video.md#getframedecodingparameters)
>
> ### Delegate
> <hr>
> * [setDBRErrorDelegate](primary-video.md#setdbrerrordelegate)
> * [setDBRTextResultDelegate](primary-video.md#setdbrtextresultdelegate)
> * [setDBRIntermdeiateResultDelegate](primary-video.md#setdbrintermdeiateresultdelegate)
>
> ### Status retrieval
> <hr>
> * [getLengthOfFrameQueue](primary-video.md#getlengthofframequeue)
