---
layout: default-layout
title: Dynamsoft Barcode Reader for Android SDK - Release Notes v9.x
description: This is the release notes page of Dynamsoft Barcode Reader for Android SDK v9.x.
keywords: release notes, android, version 9.x,
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# Release Notes for Android SDK - 9.x

## 9.0.1 (04/19/2022)

### Fixed

- Fixed a bug that might offset the position of highlight overlays on the decoded barcodes when used together with `DynamsoftCameraEnhancer`.

## 9.0.0 (03/22/2022)

### Highlights

{%- include release-notes/product-highlight-9.0.0.md -%}

### Changelog

#### New

- Added `BF_CODE_11` under enumeration [`EnumBarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) to specify newly supported barcode format, Code 11. The enumeration value of `BF_ONED` and `BF_ALL` are updated as well.
- Added `BF2_PHARMACODE_ONE_TRACK`, `BF2_PHARMACODE_TWO_TRACK` and `BF2_PHARMACODE` under enumeration [`EnumBarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2). to specify newly supported barcode format, Pharmacode.
- Added a new error code [`DBRERR_PHARMACODE_LICENSE_INVALID`]({{ site.enumerations }}error-code.html#error-code--10062) which will be returned when the license of Pharmacode is invalid.
- Added `DRM_BROAD_WARP`, `DRM_LOCAL_REFERENCE` and `DRM_DEWRINKLE` under enumeration [`EnumDeformationResistingMode`]({{ site.enumerations }}parameter-mode-enums.html#deformationresistingmode) to apply new deformation resisting modes.
- Added a parameter [`FormatSpecification.VerifyCheckDigit`]({{ site.parameters_reference }}verify-check-digit.html).
- Added new argument [`ConfidenceThreshold`]({{ site.parameters_reference }}localization-modes.html#confidencethreshold) to the `LocalizationModes` mode arguments.
- Added static method [`BarcodeReader.initLicense`]({{ site.android_api }}primary-license.html#initlicense) to replace legacy license activation APIs. The new method will support both online and offline licenses.
- Added interface [`DBRLicenseVerificationListener`]({{ site.android_api }}interface-dbrlicenseverificationlistener.html) to get license verification callback when using `BarcodeReader.initLicense`.
- Added interface [`TextResultListener`]({{ site.android_api }}interface-textresultcallback.html).
- Added interface [`IntermediateResultListener`]({{ site.android_api }}interface-intermediateresultcallback.html).
- Added the following image [decoding methods]({{ site.android_api }}primary-decode.html). The parameter `templateName` is not required in the new methods.
  - `BarcodeReader.decodeBuffer`
  - `BarcodeReader.decodeFile`
  - `BarcodeReader.decodeFileInMemory`
  - `BarcodeReader.decodeBase64String`
  - `BarcodeReader.decodeBufferedImage`
  - `BarcodeReader.decodeIntermediateResults`

#### Fixed

- Fixed a bug that might cause a crash when using multiple threads for barcode decoding.

#### Deprecated

- The following license activation APIs are deprecated and will be removed in 10.0 release:
  - Class `DMDLSConnectionParameters`
  - Interface `DBRServerLicenseVerificationListener`
  - Interface `DBRDLSLicenseVerificationListener`
  - Enumeration `EnumDMChargeWay`
  - Enumeration `EnumDMLicenseModule`
  - Enumeration `EnumDMUUIDGenerationMethod`
  - Enumeration `EnumProduct`
  - Method `BarcodeReader.initLicenseFromServer`
  - Method `BarcodeReader.initLicenseFromLicenseContent`
  - Method `BarcodeReader.initLicenseFromDLS`
  - Method `BarcodeReader.outputLicenseToString`

- The image decoding methods with parameter templateName are deprecated
  - `BarcodeReader.decodeBuffer`
  - `BarcodeReader.decodeFile`
  - `BarcodeReader.decodeFileInMemory`
  - `BarcodeReader.decodeBase64String`
  - `BarcodeReader.decodeBufferedImage`
  - `BarcodeReader.decodeIntermediateResults`

- Interface `TextResultCallback` is deprecated.
- Interface `IntermediateResultCallback` is deprecated.

#### Breaking Changes

- Configurations of the preset templates are changed.
  - Changed the configurations of `EnumPresetTemplate.DEFAULT` to `EnumPresetTemplate.VIEDE_SINGLE_BARCODE`.
  - Added template `EnumPresetTemplate.IMAGE_DEFAULT` to store the legacy configurations of `EnumPresetTemplate.DEFAULT`.
- Removed legacy video barcode decoding APIs
  - Class `DCESettingParameters`
  - Class `FrameDecodingParameters`
  - Enumeration `EnumClarityCalculationMethod`
  - Enumeration `EnumClarityFilterMode`
  - Interface `ErrorCallback`
  - Method `BarcodeReader.SetCameraEnhancerParam`
  - Method `BarcodeReader.StartCameraEnhancer`
  - Method `BarcodeReader.StopCameraEnhancer`
  - Method `BarcodeReader.PauseCameraEnhancer`
  - Method `BarcodeReader.ResumeCameraEnhancer`
  - Method `BarcodeReader.startFrameDecoding`
  - Method `BarcodeReader.startFrameDecodingEx`
  - Method `BarcodeReader.appendFrame`
  - Method `BarcodeReader.setErrorCallback`
  - Method `BarcodeReader.stopFrameDecoding`
  - Method `BarcodeReader.initFrameDecodingParameters`
  - Method `BarcodeReader.getLenghtOfFrameQueue`

- Removed the following legacy license activation APIs
  - Interface `DMLTSConnectionParameters`
  - Protocol `DBRLTSLicenseVerificationListener`
  - Method `initLicenseFromLTS`
