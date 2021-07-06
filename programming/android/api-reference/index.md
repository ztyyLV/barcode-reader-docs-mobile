---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Main Page
description: This is the main page of Dynamsoft Barcode Reader for Android SDK API Reference.
keywords: api reference, android
needAutoGenerateSidebar: true
noTitleIndex: true
needGenerateH3Content: true
breadcrumbText: API Reference
---

# Dynamsoft Barcode Reader SDK - Android API Reference

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ## BarcodeReader Class
> ### Initialize and Destroy
> <hr>
> * [BarcodeReader](primary-initialize-and-destroy.md#barcodereader)
> * [destroy](primary-initialize-and-destroy.md#destroy)
>
> ### Decode
> <hr>
> * [decodeFile](primary-decode.md#decodefile)
> * [decodeFileInMemory](primary-decode.md#decodefileinmemory)
> * [decodeBuffer](primary-decode.md#decodebuffer)
> * [decodeBase64String](primary-decode.md#decodebase64string)
> * [decodeBufferedImage](primary-decode.md#decodebufferedimage)
> * [initIntermediateResult](primary-decode.md#initintermediateresult)
> * [decodeIntermediateResults](primary-decode.md#decodeintermediateresults)
>
> ### License
> <hr>
> * [initLicense](primary-license.md#initlicense)
> * [initLicenseFromServer](primary-license.md#initlicensefromserver)
> * [initLicenseFromLicenseContent](primary-license.md#initlicensefromlicensecontent)
> * [outputLicenseToString](primary-license.md#outputlicensetostring)
> * [initLicenseFromLTS](primary-license.md#initlicensefromlts)
>
> ### Camera Enhancer
> <hr>
> * [StartCameraEnhancer](primary-camera.md#start-stop-pause-resume-camera-enhancer)
> * [StopCameraEnhancer](primary-camera.md#start-stop-pause-resume-camera-enhancer)
> * [PauseCameraEnhancer](primary-camera.md#start-stop-pause-resume-camera-enhancer)
> * [ResumeCameraEnhancer](primary-camera.md#start-stop-pause-resume-camera-enhancer)
> * [SetCameraEnhancerParam](primary-camera.md#setcameraenhancerparam)
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
>
> #### Advanced
> <hr>
> * [initRuntimeSettingsWithFile](primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithfile)
> * [initRuntimeSettingsWithString](primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithstring)
> * [appendTplFileToRuntimeSettings](primary-parameter-and-runtime-settings-advanced.md#appendtplfiletoruntimesettings)
> * [appendTplStringToRuntimeSettings](primary-parameter-and-runtime-settings-advanced.md#appendtplstringtoruntimesettings)
> * [getAllParameterTemplateNames](primary-parameter-and-runtime-settings-advanced.md#getallparametertemplatenames)
> * [outputSettingsToFile](primary-parameter-and-runtime-settings-advanced.md#outputsettingstofile)
> * [outputSettingsToString](primary-parameter-and-runtime-settings-advanced.md#outputsettingstostring)
>
> ### Result
> <hr>
> * [getIntermediateResults](primary-result.md#getintermediateresults)
>
> ### Status Retrieval
> <hr>
> * [getVersion](primary-status-retrieval.md#getversion)
>
> ### Video
>
> #### Decode
> <hr>
> * [startFrameDecoding](primary-video.md#startframedecoding)
> * [startFrameDecodingEx](primary-video.md#startframedecodingex)
> * [appendFrame](primary-video.md#appendframe)
> * [stopFrameDecoding](primary-video.md#stopframedecoding)
>
> #### Parameter
> <hr>
> * [initFrameDecodingParameters](primary-video.md#initframedecodingparameters)
>
> #### Callback
> <hr>
> * [setErrorCallback](primary-video.md#seterrorcallback)
> * [setTextResultCallback](primary-video.md#settextresultcallback)
> * [setIntermediateResultCallback](primary-video.md#setintermediateresultcallback)
>
> #### Status retrieval
> <hr>
> * [getLengthOfFrameQueue](primary-video.md#getlengthofframequeue)



<div class="doc-card-prefix doc-card-list-prefix"></div>

> ## Interface
> <hr>
> * [ErrorCallback](interface.md#errorcallback)
> * [IntermediateResultCallback](interface.md#intermediateresultcallback)
> * [TextResultCallback](interface.md#textresultcallback)
> * [DBRServerLicenseVerificationListener](interface.md#dbrserverlicenseverificationlistener)
> * [DBRLTSLicenseVerificationListener](interface.md#dbrltslicenseverificationlistener)

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ## Error Code
> <hr>
> * [ErrorCode]({{ site.enumerations }}error-code.html)

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ## Auxiliary Classes
> <hr>
> * [AztecDetails](auxiliary-AztecDetails.md)
> * [BarcodeReaderException](auxiliary-BarcodeReaderException.md)
> * [Contour](auxiliary-Contour.md)
> * [DataMatrixDetails](auxiliary-DataMatrixDetails.md)
> * [DCESettingParameters](auxiliary-DCESettingParameters.md)
> * [DMLTSConnectionParameters](auxiliary-DMLTSConnectionParameters.md)
> * [ExtendedResult](auxiliary-ExtendedResult.md)
> * [FrameDecodingParameters](auxiliary-FrameDecodingParameters.md)
> * [FurtherModes](auxiliary-FurtherModes.md)
> * [ImageData](auxiliary-ImageData.md)
> * [IntermediateResult](auxiliary-IntermediateResult.md)
> * [LineSegment](auxiliary-LineSegment.md)
> * [LocalizationResult](auxiliary-LocalizationResult.md)
> * [OneDCodeDetails](auxiliary-OneDCodeDetails.md)
> * [PDF417Details](auxiliary-PDF417Details.md)
> * [PublicRuntimeSettings](auxiliary-PublicRuntimeSettings.md)
> * [QRCodeDetails](auxiliary-QRCodeDetails.md)
> * [Quadrilateral](auxiliary-Quadrilateral.md)
> * [RegionDefinition](auxiliary-RegionDefinition.md)
> * [RegionOfInterest](auxiliary-RegionOfInterest.md)
> * [SamplingImageData](auxiliary-SamplingImageData.md)
> * [TextResult](auxiliary-TextResult.md)
>

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ## Enumerations
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
