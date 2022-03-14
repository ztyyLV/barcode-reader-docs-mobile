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

## 9.0.0 (03/17/2022)

### Changelog

#### New

- Added `BF_CODE_11` under enumeration `BarcodeFormat` to specify newly supported barcode format, Code 11. The enumeration value of `BF_ONED` and `BF_ALL` are updated as well.
- Added `BF2_PHARMACODE_ONE_TRACK`, `BF2_PHARMACODE_TWO_TRACK` and `BF2_PHARMACODE` under enumeration BarcodeFormat2. to specify newly supported barcode format, Pharmacodes. Added a new error code `DBRERR_PHARMACODE_LICENSE_INVALID` which will be returned when the license of Pharmacode is invalid.
- Added `DRM_BROAD_WARP`, `DRM_LOCAL_REFERENCE` and `DRM_DEWRINKLE` under enumeration `EnumDeformationResistingMode` to apply new deformation resisting modes.
- Added static method `BarcodeReader.initLicense` to replace legacy license activation APIs. The new method will support both online and offline license.
- Added interface `DBRLicenseVerificationListener` to get license verification callback when using `BarcodeReader.initLicense`.
- Added interface `TextResultListener`.
- Added interface `IntermediateResultListener`.
- Added the following image decoding methods. The parameter `templateName` is not required in the new methods.
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

- Removed legacy video barcode decoding APIs
  - Class `DCESettingParameters`
  - Class `FrameDecodingParameters`
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
