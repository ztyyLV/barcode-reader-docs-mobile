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

### Changelog

#### New

- Added `EnumBarcodeFormatCODE11` under enumeration `BarcodeFormat` to specify newly supported barcode format, Code 11. The enumeration value of `EnumBarcodeFormatONED` and `EnumBarcodeFormatALL` are updated as well.
- Added `EnumBarcodeFormat2PHARMACODEONETRACK`, `EnumBarcodeFormat2PHARMACODETWOTRACK` and `EnumBarcodeFormat2PHARMACODE` under enumeration `BarcodeFormat2`. to specify newly supported barcode format, Pharmacodes. Added a new error code `DBRERR_PHARMACODE_LICENSE_INVALID` which will be returned when the license of Pharmacode is invalid.
- Added `EnumDeformationResistingModeBroadWarp`, `EnumDeformationResistingModeLocalReference` and `EnumDeformationResistingModeDewrinkle` under enumeration `EnumDeformationResistingMode` to apply new deformation resisting modes.
- Added static method `DynamsoftBarcodeReader.initLicense` to replace legacy license activation APIs.
- Added protocol `DBRLicenseVerificationListener` to replace `DMDLSLicenseVerificationDelegate`
- Added protocol `DBRTextResultListener` to replace `DBRTextResultDelegate`
- Added protocol `DBRIntermediateResultListener` to replact `DBRIntermediateResultDelegate`
- Added the following image decoding methods. The parameter `templateName` is not required in the new methods.
  - `DynamsoftBarcodeReader.decodeBuffer`
  - `DynamsoftBarcodeReader.decodeImage`
  - `DynamsoftBarcodeReader.decodeFileWithName`
  - `DynamsoftBarcodeReader.decodeBase64`
  - `DynamsoftBarcodeReader.decodeIntermediateResult`

#### Fixed

- Fixed a bug that might change the hard binding UUID.
- Fixed a bug that might cause a crash when using multiple threads for barcode decoding.

#### Deprecated

- The following license activation APIs are deprecated:
  - Interface `iDMDLSConnectionParameters`
  - Protocol `DBRServerLicenseVerificationDelegate`
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
