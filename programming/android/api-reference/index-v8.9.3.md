---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Main Page
description: This is the main page of Dynamsoft Barcode Reader for Android SDK API Reference.
keywords: api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
breadcrumbText: Android API Reference
noTitleIndex: true
pageStartVer: 8.6
---

# Android API Reference

## BarcodeReader Class

### Initialize

  | Method               | Description |
  |----------------------|-------------|
  | [`BarcodeReader`](primary-initialize-and-destroy.md#barcodereader) | Initialization of `BarcodeReader` object.|

### Video Decoding Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`setCameraEnhancer`](primary-video.md#setcameraenhancer) | Bind a Camera Enhancer instance to the Barcode Reader.  |
  | [`startScanning`](primary-video.md#startscanning) | Start the barcode reading thread. |
  | [`stopScanning`](primary-video.md#stopscanning) | Stop the barcode reading thread. |
  | [`setTextResultCallback`](primary-video.md#settextresultcallback) | Set callback interface to process text results generated during frame decoding. |
  | [`setIntermediateResultCallback`](primary-video.md#setintermediateresultcallback) | Set callback interface to process intermediate results generated during frame decoding. |

### Image Decoding Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`decodeBuffer`](primary-decode.md#decodebuffer) | Decode barcodes from raw buffer. |
  | [`decodeFile`](primary-decode.md#decodefile) | Decode barcodes from a specified image file. |
  | [`decodeFileInMemory`](primary-decode.md#decodefileinmemory) | Decode barcodes from an image file in memory. |
  | [`decodeBase64String`](primary-decode.md#decodebase64string) | Decode barcodes from a base64 encoded string. |
  | [`decodeBufferedImage`](primary-decode.md#decodebufferedimage) | Decodes barcode from a buffered image (bitmap). |
  | [`initIntermediateResult`](primary-decode.md#initintermediateresult) | Inits an intermediateResult struct with default values. |
  | [`decodeIntermediateResults`](primary-decode.md#decodeintermediateresults) | Decodes barcode from intermediate results. |

### License
  
  | Method               | Description |
  |----------------------|-------------|
  | [`initLicense`](primary-license.md#initlicense) | Read product key and activate the SDK. |
  | [`initLicenseFromServer`](primary-license.md#initlicensefromserver) | Initialize license and connect to the specified server for online verification. |
  | [`initLicenseFromLicenseContent`](primary-license.md#initlicensefromlicensecontent) | Initialize license from the license content on client machine for offline verification. |
  | [`outputLicenseToString`](primary-license.md#outputlicensetostring) | Output the license content to a string from the license server. |
  | [`initLicenseFromDLS`](primary-license.md#initlicensefromdls) | Initializes the barcode reader license and connects to the specified server for online verification. |
  | [`initLicenseFromLTS`](primary-license.md#initlicensefromlts) | `Deprecated`, please use [`initLicenseFromDLS`](primary-license.md#initlicensefromdls) instead. |

### Parameter and Runtime Settings

#### Basic

  | Method               | Description |
  |----------------------|-------------|
  | [`getRuntimeSettings`](primary-parameter-and-runtime-settings-basic.md#getruntimesettings) | Get current runtime settings. |
  | [`updateRuntimeSettings (with struct)`](primary-parameter-and-runtime-settings-basic.md#updateruntimesettings) | Modify and update the current runtime settings. |
  | [`updateRuntimeSettings (with preset template)`](primary-parameter-and-runtime-settings-basic.md#with-a-preset-template) | Update runtime settings from one of the preset templates. |
  | [`resetRuntimeSettings`](primary-parameter-and-runtime-settings-basic.md#resetruntimesettings) | Reset runtime settings to default. |

#### Advanced
  
  | Method               | Description |
  |----------------------|-------------|
  | [`initRuntimeSettingsWithFile`](primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithfile)  | Initialize runtime settings with the settings in a given JSON file. |
  | [`initRuntimeSettingsWithString`](primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithstring) | Initialize runtime settings with the settings in a given JSON string. |
  | [`appendTplFileToRuntimeSettings`](primary-parameter-and-runtime-settings-advanced.md#appendtplfiletoruntimesettings) | Append a new template file to the current runtime settings. |
  | [`appendTplStringToRuntimeSettings`](primary-parameter-and-runtime-settings-advanced.md#appendtplstringtoruntimesettings) | Append a new template string to the current runtime settings. |
  | [`getAllParameterTemplateNames`](primary-parameter-and-runtime-settings-advanced.md#getallparametertemplatenames) | Gets the parameter templates name array. |
  | [`outputSettingsToFile`](primary-parameter-and-runtime-settings-advanced.md#outputsettingstofile) | Output runtime settings to a settings file (JSON file). |
  | [`outputSettingsToString`](primary-parameter-and-runtime-settings-advanced.md#outputsettingstostring) | Output runtime settings to a string. |
  | [`setModeArgument`](primary-parameter-and-runtime-settings-advanced.md#setmodeargument) | Set argument value for the specified mode parameter. |
  | [`getModeArgument`](primary-parameter-and-runtime-settings-advanced.md#getmodeargument) | Get argument value for the specified mode parameter. |

### Result

  | Method               | Description |
  |----------------------|-------------|
  | [`getIntermediateResults`](primary-result.md#getintermediateresults) | Get intermediate results. |
  | [`enableResultVerification`](primary-result.md#enableresultverification) | Verify the results before output. |
  | [`enableDuplicateFiter`](primary-result.md#enableduplicatefiter) | Output the duplicated result only once for every 3 seconds. |

### Status Retrieval

  | Method               | Description |
  |----------------------|-------------|
  | [`getVersion`](primary-status-retrieval.md#getversion) | Get version information of SDK.|

### Camera Enhancer
  
   | Method               | Description |
   |----------------------|-------------|
   | [`StartCameraEnhancer`](primary-camera.md#startcameraenhancer) | Deprecated, use [`startScanning`](primary-video.md#startscanning) instead. |
   | [`StopCameraEnhancer`](primary-camera.md#stopcameraenhancer) | Deprecated, use [`stopScanning`](primary-video.md#stopscanning) instead. |
   | [`PauseCameraEnhancer`](primary-camera.md#pausecameraenhancer) | Deprecated, use [`stopScanning`](primary-video.md#stopscanning) instead. |
   | [`ResumeCameraEnhancer`](primary-camera.md#resumecameraenhancer) | Deprecated, use [`startScanning`](primary-video.md#startscanning) instead. |
   | [`SetCameraEnhancerParam`](primary-camera.md#setcameraenhancerparam) | Deprecated, use [`setCameraEnhancer`](primary-video.md#setcameraenhancer) instead. |

## [Error Code]({{ site.enumerations }}error-code.html)

## Auxiliary Classes

- [`AztecDetails`](auxiliary-AztecDetails.md)
- [`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)
- [`Contour`](auxiliary-Contour.md)
- [`DataMatrixDetails`](auxiliary-DataMatrixDetails.md)
- [`DMLTSConnectionParameters`](auxiliary-DMLTSConnectionParameters.md)
- [`ExtendedResult`](auxiliary-ExtendedResult.md)
- [`FurtherModes`](auxiliary-FurtherModes.md)
- [`ImageData`](auxiliary-ImageData.md)
- [`IntermediateResult`](auxiliary-IntermediateResult.md)
- [`LineSegment`](auxiliary-LineSegment.md)
- [`LocalizationResult`](auxiliary-LocalizationResult.md)
- [`OneDCodeDetails`](auxiliary-OneDCodeDetails.md)
- [`PDF417Details`](auxiliary-PDF417Details.md)
- [`PublicRuntimeSettings`](auxiliary-PublicRuntimeSettings.md)
- [`QRCodeDetails`](auxiliary-QRCodeDetails.md)
- [`Quadrilateral`](auxiliary-Quadrilateral.md)
- [`RegionDefinition`](auxiliary-RegionDefinition.md)
- [`RegionOfInterest`](auxiliary-RegionOfInterest.md)
- [`SamplingImageData`](auxiliary-SamplingImageData.md)
- [`TextResult`](auxiliary-TextResult.md)

## Interfaces

  | Interfaces | Description |
  |----------|-------------|
  | [`TextResultCallback`](interface-textresultcallback.md) | The interface to handle callback when text results are returned. |
  | [`IntermediateResultCallback`](interface-intermediateresultcallback.md) | The interface to handle callback when intermediate results are returned. |
  | [`ErrorCallback`](interface-errorcallback.md) | The interface to handle callback when an error is returned. |
  | [`DBRServerLicenseVerificationListener`](interface-dbrserverlicenseverificationlistener.md) | The interface to handle callback when license verification messages are returned. |
  | [`DBRDLSLicenseVerificationListener`](interface-dbrdlslicenseverificationlistener.md) | The interface to handle callback when license verification messages are returned. |

## Enumerations

- [`EnumAccompanyingTextRecognitionMode`]({{ site.enumerations }}parameter-mode-enums.html#accompanyingtextrecognitionmode)
- [`EnumBarcodeColourMode`]({{ site.enumerations }}parameter-mode-enums.html#barcodecolourmode)
- [`EnumBarcodeComplementMode`]({{ site.enumerations }}parameter-mode-enums.html#barcodecomplementmode)
- [`EnumBarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat)
- [`EnumBarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2)
- [`EnumBinarizationMode`]({{ site.enumerations }}parameter-mode-enums.html#binarizationmode)
- [`EnumClarityCalculationMethod`]({{ site.enumerations }}frame-decoding-enums.html#claritycalculationmethod)
- [`EnumClarityFilterMode`]({{ site.enumerations }}frame-decoding-enums.html#clarityfiltermode)
- [`EnumColourClusteringMode`]({{ site.enumerations }}parameter-mode-enums.html#colourclusteringmode)
- [`EnumColourConversionMode`]({{ site.enumerations }}parameter-mode-enums.html#colourconversionmode)
- [`EnumConflictMode`]({{ site.enumerations }}parameter-mode-enums.html#conflictmode)
- [`EnumDeblurMode`]({{ site.enumerations }}parameter-mode-enums.html#deblurmode)
- [`EnumDeformationResistingMode`]({{ site.enumerations }}parameter-mode-enums.html#deformationresistingmode)
- [`EnumDMChargeWay`]({{ site.enumerations }}other-enums.html#dm_chargeway)
- [`EnumDMLicenseModule`]({{ site.enumerations }}other-enums.html#dm_licensemodule)
- [`EnumDMUUIDGenerationMethod`]({{ site.enumerations }}other-enums.html#dm_uuidgenerationmethod)
- [`EnumDPMCodeReadingMode`]({{ site.enumerations }}parameter-mode-enums.html#dpmcodereadingmode)
- [`EnumGrayscaleTransformationMode`]({{ site.enumerations }}parameter-mode-enums.html#grayscaletransformationmode)
- [`EnumImagePixelFormat`]({{ site.enumerations }}other-enums.html#imagepixelformat)
- [`EnumImagePreprocessingMode`]({{ site.enumerations }}parameter-mode-enums.html#imagepreprocessingmode)
- [`EnumIMResultDataType`]({{ site.enumerations }}result-enums.html#imresultdatatype)
- [`EnumIntermediateResultSavingMode`]({{ site.enumerations }}result-enums.html#intermediateresultsavingmode)
- [`EnumIntermediateResultType`]({{ site.enumerations }}result-enums.html#intermediateresulttype)
- [`EnumLocalizationMode`]({{ site.enumerations }}parameter-mode-enums.html#localizationmode)
- [`EnumPDFReadingMode`]({{ site.enumerations }}parameter-mode-enums.html#pdfreadingmode)
- [`EnumQRCodeErrorCorrectionLevel`]({{ site.enumerations }}other-enums.html#qrcodeerrorcorrectionlevel)
- [`EnumRegionPredetectionMode`]({{ site.enumerations }}parameter-mode-enums.html#regionpredetectionmode)
- [`EnumResultCoordinateType`]({{ site.enumerations }}result-enums.html#resultcoordinatetype)
- [`EnumResultType`]({{ site.enumerations }}result-enums.html#resulttype)
- [`EnumScaleUpMode`]({{ site.enumerations }}parameter-mode-enums.html#scaleupmode)
- [`EnumTerminatePhase`]({{ site.enumerations }}parameter-mode-enums.html#terminatephase)
- [`EnumTextFilterMode`]({{ site.enumerations }}parameter-mode-enums.html#textfiltermode)
- [`EnumTextResultOrderMode`]({{ site.enumerations }}result-enums.html#textresultordermode)
- [`EnumTextureDetectionMode`]({{ site.enumerations }}parameter-mode-enums.html#texturedetectionmode)
- [`EnumPresetTemplate`]({{ site.enumerations }}other-enums.html#enumpresettemplate)
