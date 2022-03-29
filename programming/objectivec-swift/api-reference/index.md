---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Main Page
description: This is the main page of Dynamsoft Barcode Reader for iOS SDK API Reference.
keywords: api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
breadcrumbText: iOS API Reference
---

# API Reference - iOS

## DynamsoftBarcodeReader Class

### Initialize
  
  | Method               | Description |
  |----------------------|-------------|
  | [`init`](primary-initialize.md#init) | Create an instance of Dynamsoft Barcode Reader. |
  | [`dispose`](primary-initialize.md#dispose) | Destroy the instance of Dynamsoft Barcode Reader. |

&nbsp;

### Video decoding Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`setCameraEnhancer`](primary-video.md#setcameraenhancer) | Bind a Camera Enhancer instance to the Barcode Reader.  |
  | [`startScanning`](primary-video.md#startscanning) | Start the barcode reading thread. |
  | [`stopScanning`](primary-video.md#stopscanning) | Stop the barcode reading thread. |
  | [`setDBRTextResultListener`](primary-video.md#setdbrtextresultlistener) | Set callback function to process text results generated during frame decoding. |
  | [`setDBRIntermediateResultListener`](primary-video.md#setdbrintermediateresultlistener) | Set callback function to process intermediate results generated during frame decoding. |

> Note:
>
> - `setDBRTextResultDelegate` is deprecated, please use `setDBRTextResultListener` instead.
> - `setDBRIntermediateResultDelegate` is deprecated, please use `setDBRIntermediateResultListener` instead.

&nbsp;

### Image decoding Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`decodeBuffer`](primary-decode.md#decodebuffer) | Decode barcodes from raw buffer. |
  | [`decodeFileWithName`](primary-decode.md#decodefilewithname) | Decode barcodes from a specified image file. |
  | [`decodeImage`](primary-decode.md#decodeimage) | Decode barcodes from an image file in memory. |
  | [`decodeBase64`](primary-decode.md#decodebase64) | Decode barcodes from a base64 encoded string. |
  | [`createIntermediateResult`](primary-decode.md#createintermediateresult) | Inits an intermediateResult struct with default values. |
  | [`decodeIntermediateResults`](primary-decode.md#decodeintermediateresults) | Decodes barcode from intermediate results. |

&nbsp;

### License

  | Method               | Description |
  |----------------------|-------------|
  | [`initLicense`](primary-license.md#initlicense) | Read product key and activate the SDK. |

> Note:  
>  
> The following license activation methods are deprecated:
>
> - `license`
> - `outputLicenseToString`
> - `initLicenseFromDLS`
> - `initWithLicenseFromServer`
>
> Please use [`initLicense`](primary-license.md#initlicense) to activate the license.

&nbsp;

### Parameter and Runtime Settings

#### Basic
  
  | Method               | Description |
  |----------------------|-------------|
  | [`setModeArgument`](primary-parameter-and-runtime-settings-basic.md#setmodeargument) | Set argument value for the specified mode parameter. |
  | [`getModeArgument`](primary-parameter-and-runtime-settings-basic.md#getmodeargument) | Get argument value for the specified mode parameter. |
  | [`getRuntimeSettings`](primary-parameter-and-runtime-settings-basic.md#getruntimesettings) | Get current runtime settings. |
  | [`updateRuntimeSettings (with struct)`](primary-parameter-and-runtime-settings-basic.md#updateruntimesettings) | Modify and update the current runtime settings. |
  | [`updateRuntimeSettings (with preset template)`](primary-parameter-and-runtime-settings-basic.md#with-a-preset-template) | Update runtime settings from one of the preset templates. |
  | [`resetRuntimeSettings`](primary-parameter-and-runtime-settings-basic.md#resetruntimesettings) | Reset runtime settings to default. |

&nbsp;

#### Advanced

  | Method               | Description |
  |----------------------|-------------|
  | [`initRuntimeSettingsWithFile`](primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithfile) | Initialize runtime settings with the settings in a given JSON file. |
  | [`initRuntimeSettingsWithString`](primary-parameter-and-runtime-settings-advanced.md#initruntimesettingswithstring) | Initialize runtime settings with the settings in a given JSON string. |
  | [`appendTplFileToRuntimeSettings`](primary-parameter-and-runtime-settings-advanced.md#appendtplfiletoruntimesettings) | Append a new template file to the current runtime settings. |
  | [`appendTplStringToRuntimeSettings`](primary-parameter-and-runtime-settings-advanced.md#appendtplstringtoruntimesettings) | Append a new template string to the current runtime settings. |
  | [`allParameterTemplateNames`](primary-parameter-and-runtime-settings-advanced.md#allparametertemplatenames) | Get the count of the parameter templates. |
  | [`outputSettingsToFile`](primary-parameter-and-runtime-settings-advanced.md#outputsettingstofile) | Output runtime settings to a settings file (JSON file). |
  | [`outputSettingsToString`](primary-parameter-and-runtime-settings-advanced.md#outputsettingstostring) | Output runtime settings to a string. |

&nbsp;

### Result

  | Method               | Description |
  |----------------------|-------------|
  | [`getIntermediateResult`](primary-result.md#getintermediateresult) | Get intermediate results. |

&nbsp;

## Auxiliary Classes

- [`iAztecDetails`](auxiliary-iAztecDetails.md)
- [`iContour`](auxiliary-iContour.md)
- [`iDataMatrixDetails`](auxiliary-iDataMatrixDetails.md)
- [`iDBRPoint`](auxiliary-iDBRPoint.md)
- [`iExtendedResult`](auxiliary-iExtendedResult.md)
- [`iFurtherModes`](auxiliary-iFurtherModes.md)
- [`iImageData`](auxiliary-iImageData.md)
- [`iIntermediateResult`](auxiliary-iIntermediateResult.md)
- [`iLineSegment`](auxiliary-iLineSegment.md)
- [`iLocalizationResult`](auxiliary-iLocalizationResult.md)
- [`iOneDCodeDetails`](auxiliary-iOneDCodeDetails.md)
- [`iPDF417Details`](auxiliary-iPDF417Details.md)
- [`iPublicRuntimeSettings`](auxiliary-iPublicRuntimeSettings.md)
- [`iQRCodeDetails`](auxiliary-iQRCodeDetails.md)
- [`iQuadrilateral`](auxiliary-iQuadrilateral.md)
- [`iRegionDefinition`](auxiliary-iRegionDefinition.md)
- [`iRegionOfInterest`](auxiliary-iRegionOfInterest.md)
- [`iSamplingImageData`](auxiliary-iSamplingImageData.md)
- [`iTextResult`](auxiliary-iTextResult.md)

> Note:  
>
> - `iDMDLSConnectionParameters` is deprecated due to the update of the license. Please use the method [`initLicense`](primary-license.md#initlicense) to activate the license instead.

&nbsp;

## Protocol

  | Protocol | Description |
  | -------- | ----------- |
  | [`DBRTextResultListener`]({{ site.oc_api }}protocol-dbrtextresultdelegate.html) | Protocol for a delegate to handle callback when text result returned. |
  | [`DBRIntermediateResultListener`]({{ site.oc_api }}protocol-dbrintermediateresultdelegate.html) | Protocol for a delegate to handle callback when intermediate result returned. |
  | [`DBRLicenseVerificationDelegate`]({{ site.oc_api }}protocol-dmdlslicenseverificationdelegate.html) | Protocol for a delegate to handle callback when license verification message returned. |

> Note:  
>  
> - `DBRTextResultDelegate` is deprecated, please use [`DBRTextResultListener`]({{ site.oc_api }}protocol-dbrtextresultlistener.html) instead.
> - `DBRIntermediateResultDelegate` is deprecated, please use [`DBRIntermediateResultListener`]({{ site.oc_api }}protocol-dbrintermediateresultlistener.html) instead.
> - [`DBRServerLicenseVerificationDelegate`](protocol-dbrserverlicenseverificationdelegate.md) is deprecated. It handles callback when using `initWithLicenseFromServer`, which is also deprecated. Please use [`initLicense`](primary-license.md#initlicense) instead.
> - [`DMDLSLicenseVerificationDelegate`](protocol-dmdlslicenseverificationdelegate.md) is deprecated. It handles callback when using `initLicenseFromDLS`, which is also deprecated. Please use [`initLicense`](primary-license.md#initlicense) instead.

&nbsp;

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

> Note:  
>  
> The following Enumerations are deprecated and will be removed in the future.  
>  
> - [`EnumProduct`]({{ site.enumerations }}other-enums.html#product)
> - [`EnumDMChargeWay`]({{ site.enumerations }}other-enums.html#dm_chargeway)
> - [`EnumDMLicenseModule`]({{ site.enumerations }}other-enums.html#dm_licensemodule)
> - [`EnumDMUUIDGenerationMethod`]({{ site.enumerations }}other-enums.html#dm_uuidgenerationmethod)

&nbsp;

## Others

View the [Error Code]({{ site.enumerations }}error-code.html)
