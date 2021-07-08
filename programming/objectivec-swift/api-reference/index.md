---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Main Page
description: This is the main page of Dynamsoft Barcode Reader for iOS SDK API Reference.
keywords: api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
breadcrumbText: API Reference
noTitleIndex: true
---

# Dynamsoft Barcode Reader SDK - iOS API Reference

## BarcodeReader Class

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ### Initialize and Destroy
> <hr>
> * [init](primary-initialize.md)
> <hr>
>
> ### Decode
> <hr>
> * [decodeFileWithName](primary-decode.md#decodefilewithname)
> * [decodeImage](primary-decode.md#decodeimage)
> * [decodeBuffer](primary-decode.md#decodebuffer)
> * [decodeBase64](primary-decode.md#decodebase64)
> * [createIntermediateResult](primary-decode.md#createintermediateresult)
> * [decodeIntermediateResults](primary-decode.md#decodeintermediateresults)
> <hr>
>
> ### License
> <hr>
> * [initWithLicense](primary-license.md#initwithlicense)
> * [initWithLicenseFromServer](primary-license.md#initwithlicensefromserver)
> * [outputLicenseToString](primary-license.md#outputlicensetostring)
> * [initLicenseFromDLS](primary-license.md#initLicenseFromDLS)
> <hr>
>
> ### Camera Enhancer
> <hr>
> * [SetCameraEnhancerParam](primary-camera.md#setcameraenhancerparam)
> <hr>
>
> ### Parameter and Runtime Settings
>
> #### Basic
> <hr>
> * [setModeArgument](primary-parameter-and-runtime-settings-basic.md#setmodeargument)
> * [getModeArgument](primary-parameter-and-runtime-settings-basic.md#getmodeargument)
> * [getRuntimeSettings](primary-parameter-and-runtime-settings-basic.md#getruntimesettings)
> * [updateRuntimeSettings](primary-parameter-and-runtime-settings-basic.md#updateruntimesettings)
> * [resetRuntimeSettings](primary-parameter-and-runtime-settings-basic.md#resetruntimesettings)
> <hr>
>
> #### Advanced
> <hr>
> * [initRuntimeSettingsWithFile](primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithfile)
> * [initRuntimeSettingsWithString](primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithstring)
> * [appendTplFileToRuntimeSettings](primary-parameter-and-runtime-settings-advanced.md#appendtplfiletoruntimesettings)
> * [appendTplStringToRuntimeSettings](primary-parameter-and-runtime-settings-advanced.md#appendtplstringtoruntimesettings)
> * [allparametertemplatenames](primary-parameter-and-runtime-settings-advanced.md#allparametertemplatenames)
> * [outputSettingsToFile](primary-parameter-and-runtime-settings-advanced.md#outputsettingstofile)
> * [outputSettingsToString](primary-parameter-and-runtime-settings-advanced.md#outputsettingstostring)
> <hr>
>
> ### Result
> <hr>
> * [getIntermediateResults](primary-result.md#getintermediateresults)
> * [enableResultVerification](primary-result.md#enableresultverification)
> * [enableDuplicateFilter](primary-result.md#enableduplicatefilter)
> <hr>
>
> ### Video
> <hr>
> * [startFrameDecoding](primary-video.md#startframedecoding)
> * [startFrameDecodingEx](primary-video.md#startframedecodingex)
> * [appendFrame](primary-video.md#appendframe)
> * [stopFrameDecoding](primary-video.md#stopframedecoding)
> * [getFrameDecodingParameters](primary-video.md#getframedecodingparameters)
> * [setDBRErrorDelegate](primary-video.md#setdbrerrordelegate)
> * [setDBRTextResultDelegate](primary-video.md#setdbrtextresultdelegate)
> * [setDBRIntermdeiateResultDelegate](primary-video.md#setdbrintermdeiateresultdelegate)
> * [getLengthOfFrameQueue](primary-video.md#getlengthofframequeue)

## Error Codes

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ### ErrorCode References
> <hr>
> * [ErrorCode]({{ site.enumerations }}error-code.html)

## Auxiliary Classes

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ### License Activation Class
> <hr>
> * [iDMDLSConnectionParameters](auxiliary-iDMDLSConnectionParameters.md)
> <hr>
> ### Parameter Configeration Classes
> <hr>
> * [iPublicRuntimeSettings](auxiliary-iPublicRuntimeSettings.md)
> * [iDCESettingParameters](auxiliary-iDCESettingParameters.md)
> * [iFrameDecodingParameters](auxiliary-iFrameDecodingParameters.md)
> * [iFurtherModes](auxiliary-iFurtherModes.md)
> <hr>
> ### Barcode Result Classes
> <hr>
> * [iTextResult](auxiliary-iTextResult.md)
> * [iAztecDetails](auxiliary-iAztecDetails.md)
> * [iExtendedResult](auxiliary-iExtendedResult.md)
> * [iDataMatrixDetails](auxiliary-iDataMatrixDetails.md)
> * [iOneDCodeDetails](auxiliary-iOneDCodeDetails.md)
> * [iPDF417Details](auxiliary-iPDF417Details.md)
> * [iQRCodeDetails](auxiliary-iQRCodeDetails.md)
> * [iLocalizationResult](auxiliary-iLocalizationResult.md)
> * [iSamplingImageData](auxiliary-iSamplingImageData.md)
> <hr>
> ### Intermediate Result Classes
> <hr>
> * [iIntermediateResult](auxiliary-iIntermediateResult.md)
> * [iContour](auxiliary-iContour.md)
> * [iImageData](auxiliary-iImageData.md)
> * [iRegionOfInterest](auxiliary-iRegionOfInterest.md)
> * [iLineSegment](auxiliary-iLineSegment.md)
> <hr>
> ### Common Classes
> <hr>
> * [iRegionDefinition](auxiliary-iRegionDefinition.md)
> * [iDBRPoint](auxiliary-iDBRPoint.md)
> * [iQuadrilateral](auxiliary-iQuadrilateral.md)

## Enumerations

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ## Enumerations List
> <hr>
> * [EnumAccompanyingTextRecognitionMode]({{ site.enumerations }}parameter-mode-enums.html#accompanyingtextrecognitionmode)
> * [EnumBarcodeColourMode]({{ site.enumerations }}parameter-mode-enums.html#barcodecolourmode)
> * [EnumBarcodeComplementMode]({{ site.enumerations }}parameter-mode-enums.html#barcodecomplementmode)
> * [EnumBarcodeFormat]({{ site.enumerations }}format-enums.html#barcodeformat)
> * [EnumBarcodeFormat_2]({{ site.enumerations }}format-enums.html#barcodeformat_2)
> * [EnumBinarizationMode]({{ site.enumerations }}parameter-mode-enums.html#binarizationmode)
> * [EnumClarityCalculationMethod]({{ site.enumerations }}frame-decoding-enums.html#claritycalculationmethod)
> * [EnumClarityFilterMode]({{ site.enumerations }}frame-decoding-enums.html#clarityfiltermode)
> * [EnumColourClusteringMode]({{ site.enumerations }}parameter-mode-enums.html#colourclusteringmode)
> * [EnumColourConversionMode]({{ site.enumerations }}parameter-mode-enums.html#colourconversionmode)
> * [EnumConflictMode]({{ site.enumerations }}parameter-mode-enums.html#conflictmode)
> * [EnumDeblurMode]({{ site.enumerations }}parameter-mode-enums.html#deblurmode)
> * [EnumDeformationResistingMode]({{ site.enumerations }}parameter-mode-enums.html#deformationresistingmode)
> * [EnumDMChargeWay]({{ site.enumerations }}other-enums.html#dm_chargeway)
> * [EnumDMLicenseModule]({{ site.enumerations }}other-enums.html#dm_licensemodule)
> * [EnumDMUUIDGenerationMethod]({{ site.enumerations }}other-enums.html#dm_uuidgenerationmethod)
> * [EnumDPMCodeReadingMode]({{ site.enumerations }}parameter-mode-enums.html#dpmcodereadingmode)
> * [EnumGrayscaleTransformationMode]({{ site.enumerations }}parameter-mode-enums.html#grayscaletransformationmode)
> * [EnumImagePixelFormat]({{ site.enumerations }}other-enums.html#imagepixelformat)
> * [EnumImagePreprocessingMode]({{ site.enumerations }}parameter-mode-enums.html#imagepreprocessingmode)
> * [EnumIMResultDataType]({{ site.enumerations }}result-enums.html#imresultdatatype)
> * [EnumIntermediateResultSavingMode]({{ site.enumerations }}result-enums.html#intermediateresultsavingmode)
> * [EnumIntermediateResultType]({{ site.enumerations }}result-enums.html#intermediateresulttype)
> * [EnumLocalizationMode]({{ site.enumerations }}parameter-mode-enums.html#localizationmode)
> * [EnumPDFReadingMode]({{ site.enumerations }}parameter-mode-enums.html#pdfreadingmode)
> * [EnumQRCodeErrorCorrectionLevel]({{ site.enumerations }}other-enums.html#qrcodeerrorcorrectionlevel)
> * [EnumRegionPredetectionMode]({{ site.enumerations }}parameter-mode-enums.html#regionpredetectionmode)
> * [EnumResultCoordinateType]({{ site.enumerations }}result-enums.html#resultcoordinatetype)
> * [EnumResultType]({{ site.enumerations }}result-enums.html#resulttype)
> * [EnumScaleUpMode]({{ site.enumerations }}parameter-mode-enums.html#scaleupmode)
> * [EnumTerminatePhase]({{ site.enumerations }}parameter-mode-enums.html#terminatephase)
> * [EnumTextFilterMode]({{ site.enumerations }}parameter-mode-enums.html#textfiltermode)
> * [EnumTextResultOrderMode]({{ site.enumerations }}result-enums.html#textresultordermode)
> * [EnumTextureDetectionMode]({{ site.enumerations }}parameter-mode-enums.html#texturedetectionmode)
