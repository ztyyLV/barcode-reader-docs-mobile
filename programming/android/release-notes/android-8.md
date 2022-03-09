---
layout: default-layout
title: Dynamsoft Barcode Reader for Android SDK - Release Notes v8.x
description: This is the release notes page of Dynamsoft Barcode Reader for Android SDK v8.x.
keywords: release notes, android, version 8.x,
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# Release Notes for Android SDK - 8.x

## 8.9.3 (03/02/2022)

- Fixed a bug that might cause memory leak when using method setTextResultCallback and setIntermediateResultCallback.
- Fixed a bug that might cause a crash on Android emulator when using it together with `DynamsoftCameraEnhancer`.

## 8.9.1 (12/28/2021)

- Fixed a bug that might affect the processing speed.

## 8.9.0 (12/16/2021)

<div class="fold-panel-prefix"></div>

### Version Highlights <i class="fa fa-caret-down"></i>

<div class="fold-panel-start"></div>

{%- include release-notes/product-highlight-8.9.0.md -%}

<div class="fold-panel-end"></div>

### Changelog

#### New

- Added method [`setCameraEnhancer`]({{ site.android_api }}primary-video.html#setcameraenhancer) to replace `SetCameraEnhancerPara` and `DCESettingParameters`. This method will simplify the binding of the Camera Enhancer to the Barcode Reader.
- Added methods [`startScanning`]({{ site.android_api }}primary-video.html#startscanning) and [`stopScanning`]({{ site.android_api }}primary-video.html#stopscanning) to control the start and stop of the video streaming barcode decoding thread. These methods are only active when using the Dynamsoft Camera Enhancer along with the Barcode Reader.
- Overwrited method [`updateRuntimeSettings`]({{ site.android_api }}primary-parameter-and-runtime-settings-basic.md#updateruntimesettings). Users can specify a member of [`EnumPresetTemplate`]({{ site.enumerations }}other-enums.html#enumpresettemplate) in the method to select a preset parameter setting template for barcode decoding.

#### Improved

- Simplified the usage of the different Modes in the `PublicRuntimeSettings` such as `LocalizationModes`, `DeblurModes`, and more. Users no longer must configure the entire Modes array to include the skipped entries as well. For example:
  - In previous versions, when you set the `DeblurModes`:

  ```java
  runtimeSettings.deblurModes = new int[]{EnumDeblurMode.DM_BASED_ON_LOC_BIN,0,0,0,0,0,0,0};
  ```

  - In v8.9 version:

  ```java
  runtimeSettings.deblurModes = new int[]{EnumDeblurMode.DM_BASED_ON_LOC_BIN};
  ```

#### Deprecated

- The following methods/class are deprecated. They are currently available but will be removed in further updates.
  - `SetCameraEnhancerPara`
  - `StartCameraEnhancer`
  - `StopCameraEnhancer`
  - `PauseCameraEnhancer`
  - `ResumeCameraEnhancer`
  - `DCESettingParameters`

## 8.8.0 (10/19/2021)

<div class="fold-panel-prefix"></div>

### Version Highlights <i class="fa fa-caret-down"></i>

<div class="fold-panel-start"></div>

{%- include release-notes/product-highlight-8.8.0.md -%}

<div class="fold-panel-end"></div>

### Changelog

#### New

- Added a new `LocalizationModes` item [`LM_ONED_FAST_SCAN`]({{site.parameters_reference}}localization-modes.html#lm_oned_fast_scan), which significantly improved the localization speed for 1D barcodes.
- Added a `TextResult` attribute `isDPM` to return whether the barcode is recognized by the DPM mode.

#### Improved

- Improved the confidence calculation algorithm for 2D barcode results. Users can get even more accurate results by configuring the confidence filter.
- Improved the barcode reading speed by applying the localized barcodes filter. The barcodes will be filtered according to the parameters [`BarcodeHeightRangeArray`]({{site.parameters_reference}}barcode-height-range-array.html), [`BarcodeWidthRangeArray`]({{site.parameters_reference}}barcode-width-range-array.html), [`BarcodeAngleRangeArray`]({{site.parameters_reference}}barcode-angle-range-array.html) and [`MinRatioOfBarcodeZoneWidthToHeight`]({{site.parameters_reference}}min-ratio-of-barcode-zone-width-to-height.html).
- Updated the exception message when the full license is invalid or has expired.

#### Breaking Change(s)

- The low confidence barcode results will no longer be returned by default. The default value of parameter [`minResultConfidence`]({{site.parameters_reference}}min-result-confidence.html) is preset to 30, which can filter out the majority of misreading results and keep as many correct results as possible.

#### API Changes

- Removed IOException from the exceptions of method [`decodeBufferedImage`]({{site.android_api}}primary-decode.html#decodebufferedimage).

#### Fixed

- Fixed a bug that might cause the application to crash when method [`StartCameraEnhancer`]({{site.android_api}}primary-camera.html#startcameraenhancer) or [`StopCameraEnhancer`]({{site.android_api}}primary-camera.html#stopcameraenhancer) is triggered more than once.

## 8.6 (07/15/2021)

<div class="fold-panel-prefix"></div>

### Version Highlights <i class="fa fa-caret-down"></i>

<div class="fold-panel-start"></div>

{%- include release-notes/product-highlight-8.6.0.md -%}

<div class="fold-panel-end"></div>

### Changelog

#### New

- Added more samples.
- Added new API `enableResultVerification`. The barcode decoding results will be verified before output if this feature is enabled. This will highly improve the accuracy of barcode scanning.
- Added new API `enableDuplicateFilter`. The barcode decoding results will be filtered before output if this feature is enabled. The duplicated results will be output only once for every three seconds.
- Added two `DeblurMode` Enumerations, `DM_BASED_ON_LOC_BIN` and `DM_SHARPENING_SMOOTHING`, to support more usage scenarios.
- Added method `initLicenseFromDLS` in `BarcodeReader` class to replace `initLicenseFromLTS`.
- Added class `DMDLSConnectionParameters` to replace class `DMLTSConnectionParameters`.
- Added interface `DBRDLSLicenseVerificationListener` and callback `DLSLicenseVerificationCallback` to replace `DBRLTSLicenseVerificationListener` and `LTSLicenseVerificationCallback`.

#### Improved

- Improved the [`confidence`]({{site.android_api}}auxiliary-ExtendedResult.html#confidence) algorithm for 1D barcode results. Users can get even more accurate results by configuring the `confidence` filter.

## 8.4 (06/08/2021)

### New

- Added a new attribute [`isMirrored`]({{site.android_class}}TextResult.html#ismirrored) to the `TextResult` class. `isMirrored` returns whether the barcode is mirrored.
- Added a new argument, `ThresholdCompensation`, to the `BinarizationModes` mode arguments.

### Improved

- Faster recognition speeds when detecting dense QR Codes.
- Improved the performance of boundary identification for DataMatrix codes.

### Deprecated

- `ThreshValueCoefficient` is now deprecated. It still works in this version but could be removed in the near future. We recommend using `ThresholdCompensation` instead.

### Fixed

- Fixed an issue that happens when calling `initLicenseFromLTS` if [`handShakeCode`]({{site.android_class}}DMLTSConnectionParameters.html#handshakecode) is not set.
- Fixed a bug when trying to build the project in the release mode with code shrinker enabled.

## 8.2.1 (05/27/2021)

### New

- [Dynamsoft Camera Enhancer (DCE)]({{site.camera}}) is now available for DBR users to quickly deploy the camera module. We added new APIs and a new class to simplify the user operations when using DBR and DCE at the same time.
- Added [Camera Enhancer setting APIs]({{site.android_methods}}camera.html#start-stop-pause-resume-camera-enhancer). These new APIs will benefit users by easily controlling the status of DCE.
- Added a new class, [`DCESettingParameters`]({{site.android_class}}DCESettingParameters.html), and a new API, [`SetCameraEnhancerParam`]({{site.android_methods}}camera.html#setcameraenhancerparam), to enable the parameter transfer between DBR and DCE. The parameter transferring will improve the focus ability of the camera.

### Improved

- Samples are updated. DCE is handling the camera-related settings in the samples.

## 8.2 (03/17/2021)

### New

- Added a new mode argument, `FindAccurateBoundary`, to [`RegionPredetectionModes`]({{ site.parameters_reference }}image-parameter/RegionPredetectionModes.html#regionpredetectionmodes) that determines if the SDK attempts to find an accurate boundary when `RegionPredetectionModes` is set to `RPM_GENERAL_HSV_CONTRAST`.
- Added a new an attribute, `organizationID` (string) to `DMLTSConnectionParameters`. The attribute adds a new layer of security for both full and trial licenses.

### Improved

- Improved both the localization and decoding algorithms for Postal Codes.
- `LocalizationMode.LM_STATISTICS_POSTAL_CODE` will not be added automatically when enabling Postal Code in your runtime settings. Instead, users must manually add it to the `LocalizationMode` array if it is required.

### Fixed

- Resolved a bug that infrequently causes the application to crash when decoding a MicroPDF417 barcode.

## 8.1.2 (01/22/2021)

### New

- Added `mode`, `page`, `totalPage` and `parityData` in the `QRCodeDetails` Class.

### Improved

- Improved the recognition accuracy for GS1 Databar.
- Removed the exception code from `barcodeText` when using a valid trial license.
- Included native C++ DLL files in the .NET assembly files, so users don't need to manually copy these files to the specific folder.

### Fixed

- Fixed a bug where `barcodeFormatString`, `barcodeFormatString_2`, `regionName` and `documentName` don't have value in the `IRT_TYPED_BARCODE_ZONE` intermediate result.

## 8.1.1 (01/19/2021)

### Fixed

- Fixed a crash issue when calling `initLicenseFromLTS` or `decode***`  methods in Android 6.x and below.

## 8.1 (01/12/2021)

### New

- Added support for MSI Code (Modified Plessey).
- Added a new member `barcodeZoneMinDistanceToImageBorders` in the `PublicRuntimeSettings` Class to set the minimum distance (in pixels) between barcode zone and image borders. Previously, it is only available in the JSON template. It can be now configured by setting `PublicRuntimeSettings` -> `barcodeZoneMinDistanceToImageBorders`.
- Added exception error message to `TextResult` when license initialization fails or decoding authorization fails.

### Improved

- Improved the localization robustness for QR Code.
- Improved the localization for low quality 1D barcodes.
- Improved the deblurring performance and recognition rate for DataMatrix.
- Improved the recognition rate for Aztec.

### Fixed

- Fixed a bug where Micro PDF417 may not be localized in multiple-barcode scenarios.
- Fixed a bug where the `ExpectedBarcodesCount` and `BarcodeFormat` parameters do not work in the `RegionDefinition`.

## 8.0 (11/17/2020)

### New

- (For `IntermediateResult` Advanced Module) Added support for decoding `IntermediateResult`. For example, users with a binarized image could use this function to skip some image preprocessing steps.
- Implemented a new licensing tracking mechanism, License 2.0, which makes it easier for users to track license usage.
- Added a new format control parameter, `BarcodeZoneMinDistanceToImageBorders`, to set the minimum distance (in pixels) between the barcode zone and image borders.
- Added a new format control parameter, `MinRatioOfBarcodeZoneWidthToHeight`, to set the minimum ratio (width/height) of the barcode zone.
- Added a new format control parameter, `BarcodeZoneBarCountRangeArray`, to set the barcode zone’s range of bar count for barcode search.
- Added a new argument, `SpatialIndexBlockSize`, for `RPM_GENERAL_RGB_CONTRAST`, `RPM_GENERAL_GRAY_CONTRAST` and `RPM_GENERAL_HSV_CONTRAST`.
- Added a new parameter, `DeblurModes`, so users can use different deblur algorithms for different scenarios. `DeblurModes` has the following enum types: `DirectBinarization`, `ThresholdBinarization`, `GrayEqulization`, `Smoothing`, `Morphing`, `DeepAnalysis` and `Sharpening`.

### Improved

- Improved the localization speed for the `ScanDirectly` mode.
- Improved the localization accuracy for DataMatrix codes with a narrow quiet zone.

### Feature Deprecated

- `DeblurLevel` is now deprecated. It still works in this version but could be removed in the near future. We recommend using `DeblurModes` instead.
