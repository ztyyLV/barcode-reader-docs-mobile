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
> * [`BarcodeReader`](BarcodeReader/initialize-and-destroy.md#barcodereader)
> * [`destroy`](BarcodeReader/initialize-and-destroy.md#destroy)
>
> ### Decode
> <hr>
> * [`decodeFile`](BarcodeReader/decode.md#decodefile)
> * [`decodeFileInMemory`](BarcodeReader/decode.md#decodefileinmemory)
> * [`decodeBuffer`](BarcodeReader/decode.md#decodebuffer)
> * [`decodeBase64String`](BarcodeReader/decode.md#decodebase64string)
> * [`decodeBufferedImage`](BarcodeReader/decode.md#decodebufferedimage)
> * [`initIntermediateResult`](BarcodeReader/decode.md#initintermediateresult)
> * [`decodeIntermediateResults`](BarcodeReader/decode.md#decodeintermediateresults)
>
> ### License
> <hr>
> * [`initLicense`](BarcodeReader/license.md#initlicense)
> * [`initLicenseFromServer`](BarcodeReader/license.md#initlicensefromserver)
> * [`initLicenseFromLicenseContent`](BarcodeReader/license.md#initlicensefromlicensecontent)
> * [`outputLicenseToString`](BarcodeReader/license.md#outputlicensetostring)
> * [`initLicenseFromLTS`](BarcodeReader/license.md#initlicensefromlts)
>
> ### Camera Enhancer
> <hr>
> * [`StartCameraEnhancer`](BarcodeReader/camera.md#start-stop-pause-resume-camera-enhancer)
> * [`StopCameraEnhancer`](BarcodeReader/camera.md#start-stop-pause-resume-camera-enhancer)
> * [`PauseCameraEnhancer`](BarcodeReader/camera.md#start-stop-pause-resume-camera-enhancer)
> * [`ResumeCameraEnhancer`](BarcodeReader/camera.md#start-stop-pause-resume-camera-enhancer)
> * [`SetCameraEnhancerParam`](BarcodeReader/camera.md#setcameraenhancerparam)
>
> ### Parameter and Runtime Settings
>
> #### Basic
> <hr>
> * [`setModeArgument`](BarcodeReader/parameter-and-runtime-settings-basic.md#setmodeargument)
> * [`getModeArgument`](BarcodeReader/parameter-and-runtime-settings-basic.md#getmodeargument)
> * [`getRuntimeSettings`](BarcodeReader/parameter-and-runtime-settings-basic.md#getruntimesettings)
> * [`updateRuntimeSettings`](BarcodeReader/parameter-and-runtime-settings-basic.md#updateruntimesettings)
> * [`resetRuntimeSettings`](BarcodeReader/parameter-and-runtime-settings-basic.md#resetruntimesettings)
>
> #### Advanced
> <hr>
> * [`initRuntimeSettingsWithFile`](BarcodeReader/parameter-and-runtime-settings-advanced.md#initruntimesettingswithfile)
> * [`initRuntimeSettingsWithString`](BarcodeReader/parameter-and-runtime-settings-advanced.md#initruntimesettingswithstring)
> * [`appendTplFileToRuntimeSettings`](BarcodeReader/parameter-and-runtime-settings-advanced.md#appendtplfiletoruntimesettings)
> * [`appendTplStringToRuntimeSettings`](BarcodeReader/parameter-and-runtime-settings-advanced.md#appendtplstringtoruntimesettings)
> * [`getAllParameterTemplateNames`](BarcodeReader/parameter-and-runtime-settings-advanced.md#getallparametertemplatenames)
> * [`outputSettingsToFile`](BarcodeReader/parameter-and-runtime-settings-advanced.md#outputsettingstofile)
> * [`outputSettingsToString`](BarcodeReader/parameter-and-runtime-settings-advanced.md#outputsettingstostring)
>
> ### Result
> <hr>
> * [`getIntermediateResults`](BarcodeReader/result.md#getintermediateresults)
>
> ### Status Retrieval
> <hr>
> * [`getVersion`](BarcodeReader/status-retrieval.md#getversion)
>
> ### Video
>
> #### Decode
> <hr>
> * [`startFrameDecoding`](BarcodeReader/video.md#startframedecoding)
> * [`startFrameDecodingEx`](BarcodeReader/video.md#startframedecodingex)
> * [`appendFrame`](BarcodeReader/video.md#appendframe)
> * [`stopFrameDecoding`](BarcodeReader/video.md#stopframedecoding)
>
> #### Parameter
> <hr>
> * [`initFrameDecodingParameters`](BarcodeReader/video.md#initframedecodingparameters)
>
> #### Callback
> <hr>
> * [`setErrorCallback`](BarcodeReader/video.md#seterrorcallback)
> * [`setTextResultCallback`](BarcodeReader/video.md#settextresultcallback)
> * [`setIntermediateResultCallback`](BarcodeReader/video.md#setintermediateresultcallback)
>
> #### Status retrieval
> <hr>
> * [`getLengthOfFrameQueue`](BarcodeReader/video.md#getlengthofframequeue)
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
> * [`AztecDetails`](class/AztecDetails.md)
> * [`BarcodeReaderException`](class/BarcodeReaderException.md)
> * [`Contour`](class/Contour.md)
> * [`DataMatrixDetails`](class/DataMatrixDetails.md)
> * [`DCESettingParameters`](class/DCESettingParameters.md)
> * [`DMLTSConnectionParameters`](class/DMLTSConnectionParameters.md)
> * [`ExtendedResult`](class/ExtendedResult.md)
> * [`FrameDecodingParameters`](class/FrameDecodingParameters.md)
> * [`FurtherModes`](class/FurtherModes.md)
> * [`ImageData`](class/ImageData.md)
> * [`IntermediateResult`](class/IntermediateResult.md)
> * [`LineSegment`](class/LineSegment.md)
> * [`LocalizationResult`](class/LocalizationResult.md)
> * [`OneDCodeDetails`](class/OneDCodeDetails.md)
> * [`PDF417Details`](class/PDF417Details.md)
> * [`PublicRuntimeSettings`](class/PublicRuntimeSettings.md)
> * [`QRCodeDetails`](class/QRCodeDetails.md)
> * [`Quadrilateral`](class/Quadrilateral.md)
> * [`RegionDefinition`](class/RegionDefinition.md)
> * [`RegionOfInterest`](class/RegionOfInterest.md)
> * [`SamplingImageData`](class/SamplingImageData.md)
> * [`TextResult`](class/TextResult.md)
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
