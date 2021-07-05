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

## BarcodeReader Class

<div class="doc-card-prefix doc-card-list-prefix"></div>

> ### Initialize and Destroy
> <hr>
> * [`BarcodeReader`](BarcodeReader/primary-initialize-and-destroy.md#barcodereader)
> * [`destroy`](BarcodeReader/primary-initialize-and-destroy.md#destroy)
>
> ### Decode
> <hr>
> * [`decodeFile`](BarcodeReader/primary-decode.md#decodefile)
> * [`decodeFileInMemory`](BarcodeReader/primary-decode.md#decodefileinmemory)
> * [`decodeBuffer`](BarcodeReader/primary-decode.md#decodebuffer)
> * [`decodeBase64String`](BarcodeReader/primary-decode.md#decodebase64string)
> * [`decodeBufferedImage`](BarcodeReader/primary-decode.md#decodebufferedimage)
> * [`initIntermediateResult`](BarcodeReader/primary-decode.md#initintermediateresult)
> * [`decodeIntermediateResults`](BarcodeReader/primary-decode.md#decodeintermediateresults)
>
> ### License
> <hr>
> * [`initLicense`](BarcodeReader/primary-license.md#initlicense)
> * [`initLicenseFromServer`](BarcodeReader/primary-license.md#initlicensefromserver)
> * [`initLicenseFromLicenseContent`](BarcodeReader/primary-license.md#initlicensefromlicensecontent)
> * [`outputLicenseToString`](BarcodeReader/primary-license.md#outputlicensetostring)
> * [`initLicenseFromLTS`](BarcodeReader/primary-license.md#initlicensefromlts)
>
> ### Camera Enhancer
> <hr>
> * [`StartCameraEnhancer`](BarcodeReader/primary-camera.md#start-stop-pause-resume-camera-enhancer)
> * [`StopCameraEnhancer`](BarcodeReader/primary-camera.md#start-stop-pause-resume-camera-enhancer)
> * [`PauseCameraEnhancer`](BarcodeReader/primary-camera.md#start-stop-pause-resume-camera-enhancer)
> * [`ResumeCameraEnhancer`](BarcodeReader/primary-camera.md#start-stop-pause-resume-camera-enhancer)
> * [`SetCameraEnhancerParam`](BarcodeReader/primary-camera.md#setcameraenhancerparam)
>
> ### Parameter and Runtime Settings
>
> #### Basic
> <hr>
> * [`setModeArgument`](BarcodeReader/primary-parameter-and-runtime-settings-basic.md#setmodeargument)
> * [`getModeArgument`](BarcodeReader/primary-parameter-and-runtime-settings-basic.md#getmodeargument)
> * [`getRuntimeSettings`](BarcodeReader/primary-parameter-and-runtime-settings-basic.md#getruntimesettings)
> * [`updateRuntimeSettings`](BarcodeReader/primary-parameter-and-runtime-settings-basic.md#updateruntimesettings)
> * [`resetRuntimeSettings`](BarcodeReader/primary-parameter-and-runtime-settings-basic.md#resetruntimesettings)
>
> #### Advanced
> <hr>
> * [`initRuntimeSettingsWithFile`](BarcodeReader/primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithfile)
> * [`initRuntimeSettingsWithString`](BarcodeReader/primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithstring)
> * [`appendTplFileToRuntimeSettings`](BarcodeReader/primary-parameter-and-runtime-settings-advanced.md#appendtplfiletoruntimesettings)
> * [`appendTplStringToRuntimeSettings`](BarcodeReader/primary-parameter-and-runtime-settings-advanced.md#appendtplstringtoruntimesettings)
> * [`getAllParameterTemplateNames`](BarcodeReader/primary-parameter-and-runtime-settings-advanced.md#getallparametertemplatenames)
> * [`outputSettingsToFile`](BarcodeReader/primary-parameter-and-runtime-settings-advanced.md#outputsettingstofile)
> * [`outputSettingsToString`](BarcodeReader/primary-parameter-and-runtime-settings-advanced.md#outputsettingstostring)
>
> ### Result
> <hr>
> * [`getIntermediateResults`](BarcodeReader/primary-result.md#getintermediateresults)
>
> ### Status Retrieval
> <hr>
> * [`getVersion`](BarcodeReader/primary-status-retrieval.md#getversion)
>
> ### Video
>
> #### Decode
> <hr>
> * [`startFrameDecoding`](BarcodeReader/primary-video.md#startframedecoding)
> * [`startFrameDecodingEx`](BarcodeReader/primary-video.md#startframedecodingex)
> * [`appendFrame`](BarcodeReader/primary-video.md#appendframe)
> * [`stopFrameDecoding`](BarcodeReader/primary-video.md#stopframedecoding)
>
> #### Parameter
> <hr>
> * [`initFrameDecodingParameters`](BarcodeReader/primary-video.md#initframedecodingparameters)
>
> #### Callback
> <hr>
> * [`setErrorCallback`](BarcodeReader/primary-video.md#seterrorcallback)
> * [`setTextResultCallback`](BarcodeReader/primary-video.md#settextresultcallback)
> * [`setIntermediateResultCallback`](BarcodeReader/primary-video.md#setintermediateresultcallback)
>
> #### Status retrieval
> <hr>
> * [`getLengthOfFrameQueue`](BarcodeReader/primary-video.md#getlengthofframequeue)
>
> ## Interface
> <hr>
> * [`ErrorCallback`](interface.md#errorcallback)
> * [`IntermediateResultCallback`](interface.md#intermediateresultcallback)
> * [`TextResultCallback`](interface.md#cb_textresult)
> * [`DBRServerLicenseVerificationListener`](interface.md#dbrserverlicenseverificationlistener)
>
> ## Error Code
> <hr>
> * [`Error Code`]({{ site.enumerations }}error-code.html)
>
> ## Classes
> <hr>
> * [`AztecDetails`](class/auxiliary-AztecDetails.md)
> * [`BarcodeReaderException`](class/auxiliary-BarcodeReaderException.md)
> * [`Contour`](class/auxiliary-Contour.md)
> * [`DataMatrixDetails`](class/auxiliary-DataMatrixDetails.md)
> * [`DCESettingParameters`](class/auxiliary-DCESettingParameters.md)
> * [`DMLTSConnectionParameters`](class/auxiliary-DMLTSConnectionParameters.md)
> * [`ExtendedResult`](class/auxiliary-ExtendedResult.md)
> * [`FrameDecodingParameters`](class/auxiliary-FrameDecodingParameters.md)
> * [`FurtherModes`](class/auxiliary-FurtherModes.md)
> * [`ImageData`](class/auxiliary-ImageData.md)
> * [`IntermediateResult`](class/auxiliary-IntermediateResult.md)
> * [`LineSegment`](class/auxiliary-LineSegment.md)
> * [`LocalizationResult`](class/auxiliary-LocalizationResult.md)
> * [`OneDCodeDetails`](class/auxiliary-OneDCodeDetails.md)
> * [`PDF417Details`](class/auxiliary-PDF417Details.md)
> * [`PublicRuntimeSettings`](class/auxiliary-PublicRuntimeSettings.md)
> * [`QRCodeDetails`](class/auxiliary-QRCodeDetails.md)
> * [`Quadrilateral`](class/auxiliary-Quadrilateral.md)
> * [`RegionDefinition`](class/auxiliary-RegionDefinition.md)
> * [`RegionOfInterest`](class/auxiliary-RegionOfInterest.md)
> * [`SamplingImageData`](class/auxiliary-SamplingImageData.md)
> * [`TextResult`](class/auxiliary-TextResult.md)
>
> ## Enumerations
> <hr>
> * [`EnumAccompanyingTextRecognitionMode`]({{ site.enumerations }}parameter-mode-enums.html#accompanyingtextrecognitionmode)
> * [`EnumBarcodeColourMode`]({{ site.enumerations }}parameter-mode-enums.html#barcodecolourmode)
> * [`EnumBarcodeComplementMode`]({{ site.enumerations }}parameter-mode-enums.html#barcodecomplementmode)
> * [`EnumBarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat)
> * [`EnumBarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2)
> * [`EnumBinarizationMode`]({{ site.enumerations }}parameter-mode-enums.html#binarizationmode)
> * [`EnumClarityCalculationMethod`]({{ site.enumerations }}frame-decoding-enums.html#claritycalculationmethod)
> * [`EnumClarityFilterMode`]({{ site.enumerations }}frame-decoding-enums.html#clarityfiltermode)
> * [`EnumColourClusteringMode`]({{ site.enumerations }}parameter-mode-enums.html#colourclusteringmode)
> * [`EnumColourConversionMode`]({{ site.enumerations }}parameter-mode-enums.html#colourconversionmode)
> * [`EnumConflictMode`]({{ site.enumerations }}parameter-mode-enums.html#conflictmode)
> * [`EnumDeblurMode`]({{ site.enumerations }}parameter-mode-enums.html#deblurmode)
> * [`EnumDeformationResistingMode`]({{ site.enumerations }}parameter-mode-enums.html#deformationresistingmode)
> * [`EnumDMChargeWay`]({{ site.enumerations }}other-enums.html#dm_chargeway)
> * [`EnumDMLicenseModule`]({{ site.enumerations }}other-enums.html#dm_licensemodule)
> * [`EnumDMUUIDGenerationMethod`]({{ site.enumerations }}other-enums.html#dm_uuidgenerationmethod)
> * [`EnumDPMCodeReadingMode`]({{ site.enumerations }}parameter-mode-enums.html#dpmcodereadingmode)
> * [`EnumGrayscaleTransformationMode`]({{ site.enumerations }}parameter-mode-enums.html#grayscaletransformationmode)
> * [`EnumImagePixelFormat`]({{ site.enumerations }}other-enums.html#imagepixelformat)
> * [`EnumImagePreprocessingMode`]({{ site.enumerations }}parameter-mode-enums.html#imagepreprocessingmode)
> * [`EnumIMResultDataType`]({{ site.enumerations }}result-enums.html#imresultdatatype)
> * [`EnumIntermediateResultSavingMode`]({{ site.enumerations }}result-enums.html#intermediateresultsavingmode)
> * [`EnumIntermediateResultType`]({{ site.enumerations }}result-enums.html#intermediateresulttype)
> * [`EnumLocalizationMode`]({{ site.enumerations }}parameter-mode-enums.html#localizationmode)
> * [`EnumPDFReadingMode`]({{ site.enumerations }}parameter-mode-enums.html#pdfreadingmode)
> * [`EnumQRCodeErrorCorrectionLevel`]({{ site.enumerations }}other-enums.html#qrcodeerrorcorrectionlevel)
> * [`EnumRegionPredetectionMode`]({{ site.enumerations }}parameter-mode-enums.html#regionpredetectionmode)
> * [`EnumResultCoordinateType`]({{ site.enumerations }}result-enums.html#resultcoordinatetype)
> * [`EnumResultType`]({{ site.enumerations }}result-enums.html#resulttype)
> * [`EnumScaleUpMode`]({{ site.enumerations }}parameter-mode-enums.html#scaleupmode)
> * [`EnumTerminatePhase`]({{ site.enumerations }}parameter-mode-enums.html#terminatephase)
> * [`EnumTextFilterMode`]({{ site.enumerations }}parameter-mode-enums.html#textfiltermode)
> * [`EnumTextResultOrderMode`]({{ site.enumerations }}result-enums.html#textresultordermode)
> * [`EnumTextureDetectionMode`]({{ site.enumerations }}parameter-mode-enums.html#texturedetectionmode)
