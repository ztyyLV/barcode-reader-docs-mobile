---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS SDK - Release Notes v9.x
description: This is the release notes page of Dynamsoft Barcode Reader for iOS SDK v9.x.
keywords: release notes, ios, 
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# Release Notes for iOS SDK - 9.x

## 9.0.0 (03/17/2022)

### Highlights

{%- include release-notes/product-highlight-9.0.0.md -%}

### Changelog

#### New

- Added `EnumBarcodeFormatCODE11` under enumeration [`EnumBarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) to specify newly supported barcode format, Code 11. The enumeration value of `EnumBarcodeFormatONED` and `EnumBarcodeFormatALL` are updated as well.
- Added `EnumBarcodeFormat2PHARMACODEONETRACK`, `EnumBarcodeFormat2PHARMACODETWOTRACK` and `EnumBarcodeFormat2PHARMACODE` under enumeration [`EnumBarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2) to specify newly supported barcode format, Pharmacodes.
- Added a new error code [`DBRERR_PHARMACODE_LICENSE_INVALID`]({{ site.enumerations }}error-code.html#error-code--10062) which will be returned when the license of Pharmacode is invalid.
- Added `EnumDeformationResistingModeBroadWarp`, `EnumDeformationResistingModeLocalReference` and `EnumDeformationResistingModeDewrinkle` under enumeration [`EnumDeformationResistingMode`]({{ site.enumerations }}parameter-mode-enums.html#deformationresistingmode) to apply new deformation resisting modes.
- Added a parameter [`FormatSpecification.VerifyCheckDigit`]({{ site.parameters_reference }}verify-check-digit.html).
- Added an Argument [`ConfidenceThreshold`]({{ site.parameters_reference }}localization-modes.html#confidencethreshold) to the `LocalizationModes` mode arguments.
- Added static method [`DynamsoftBarcodeReader.initLicense`]({{ site.oc_api }}primary-license.html#initlicense) to replace legacy license activation APIs.
- Added protocol [`DBRLicenseVerificationListener`]({{ site.oc_api }}protocol-dmdlslicenseverificationdelegate.html) to get license verification callback when using `DynamsoftBarcodeReader.initLicense`.
- Added protocol [`DBRTextResultListener`]({{ site.oc_api }}protocol-dbrtextresultdelegate.html).
- Added protocol [`DBRIntermediateResultListener`]({{ site.oc_api }}protocol-dbrintermediateresultdelegate.html).
- Added the following image [decoding methods]({{ site.oc_api }}primary-decode.html). The parameter `templateName` is not required in the new methods.
  - `DynamsoftBarcodeReader.decodeBuffer`
  - `DynamsoftBarcodeReader.decodeImage`
  - `DynamsoftBarcodeReader.decodeFileWithName`
  - `DynamsoftBarcodeReader.decodeBase64`
  - `DynamsoftBarcodeReader.decodeIntermediateResult`

#### Fixed

- Fixed a bug that might cause a crash when using multiple threads for barcode decoding.

#### Deprecated

- The following license activation APIs are deprecated:
  - Interface `iDMDLSConnectionParameters`
  - Protocol `DBRServerLicenseVerificationDelegate`
  - Protocol `DMDLSLicenseVerificationDelegate`
  - Enumeration `EnumDMChargeWay`
  - Enumeration `EnumDMLicenseModule`
  - Enumeration `EnumDMUUIDGenerationMethod`
  - Enumeration `EnumProduct`
  - Method `DynamsoftBarcodeReader.initLicenseFromServer`
  - Method `DynamsoftBarcodeReader.initLicenseFromDLS`
  - Method `DynamsoftBarcodeReader.outputLicenseToString`

- The image decoding methods with parameter templateName are deprecated
  - `DynamsoftBarcodeReader.decodeIntermediateResult`
  - `DynamsoftBarcodeReader.decodeImage`
  - `DynamsoftBarcodeReader.decodeFileWithName`
  - `DynamsoftBarcodeReader.decodeBase64`
  - `DynamsoftBarcodeReader.decodeBuffer`

- `DBRTextResultDelegate` is deprecated.
- `DBRIntermediateResultListener` is deprecated.

#### Breaking Changes

- Updated Swift APIs
  - The following method names are changed:
    - `DynamsoftBarcodeReader.updateRuntimeSettings`(with parameter `iPublicRuntimeSettings`)
    - `DynamsoftBarcodeReader.decodeIntermediateResult`
    - `DynamsoftBarcodeReader.decodeImage`
    - `DynamsoftBarcodeReader.decodeFileWithName`
    - `DynamsoftBarcodeReader.initRuntimeSettingsWithFile`
    - `DynamsoftBarcodeReader.initRuntimeSettingsWithString`
    - `DynamsoftBarcodeReader.appendTplFileToRuntimeSettings`
    - `DynamsoftBarcodeReader.appendTplStringToRuntimeSettings`
    - `DynamsoftBarcodeReader.outputSettingsToString`
    - `DynamsoftBarcodeReader.outputSettingsToFile`
  - The following methods will signal errors by returning NSErrors
    - `DynamsoftBarcodeReader.getIntermediateResult`
    - `DynamsoftBarcodeReader.createIntermediateResult`
    - `DynamsoftBarcodeReader.outputLicenseToString`
    - `DynamsoftBarcodeReader.outputSettingsToString`
    - `DynamsoftBarcodeReader.allParameterTemplateNames`
    - `DynamsoftBarcodeReader.getModeArgument`
    - `DynamsoftBarcodeReader.getRuntimeSettings`
  - The following methods will signal errors by throw exceptions
    - `DynamsoftBarcodeReader.decodeIntermediateResult`
    - `DynamsoftBarcodeReader.decodeImage`
    - `DynamsoftBarcodeReader.decodeFileWithName`
    - `DynamsoftBarcodeReader.decodeBase64`
    - `DynamsoftBarcodeReader.decodeBuffer`
  - The following methods will return an BOOL value
    - `DynamsoftBarcodeReader.updateRuntimeSettings`
    - `DynamsoftBarcodeReader.setModeArgument`
    - `DynamsoftBarcodeReader.resetRuntimeSettings`
    - `DynamsoftBarcodeReader.initRuntimeSettingsWithFile`
    - `DynamsoftBarcodeReader.initRuntimeSettingsWithString`
    - `DynamsoftBarcodeReader.appendTplFileToRuntimeSettings`
    - `DynamsoftBarcodeReader.appendTplStringToRuntimeSettings`
    - `DynamsoftBarcodeReader.outputSettingsToFile`

- Removed the following legacy video barcode decoding APIs
  - Interface `iDCESettingParameters`
  - Interface `iFrameDecodingParameters`
  - Protocol `DBRErrorDelegate`
  - Method `DynamsoftBarcodeReader.setCameraEnhancerParam`
  - Method `DynamsoftBarcodeReader.startFrameDecoding`
  - Method `DynamsoftBarcodeReader.startFrameDecodingEx`
  - Method `DynamsoftBarcodeReader.appendFrame`
  - Method `DynamsoftBarcodeReader.setDBRErrorDelegate`
  - Method `DynamsoftBarcodeReader.stopFrameDecoding`
  - Method `DynamsoftBarcodeReader.getFrameDecodingParameters`
  - Method `DynamsoftBarcodeReader.getLenghtOfFrameQueue`

- Removed the following legacy license activation APIs
  - Interface `iDMLTSConnectionParameters`
  - Protocol `DMLTSLicenseVerificationDelegate`
  - Method `DynamsoftBarcodeReader.initLicenseFromLTS`
  - Property `DynamsoftBarcodeReader.license`
