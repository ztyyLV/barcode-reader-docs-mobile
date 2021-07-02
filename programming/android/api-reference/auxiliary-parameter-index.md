---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Parameter Configurations
description: This page shows the Parameter Configurations of Dynamsoft Barcode Reader for Android SDK.
keywords: Parameter Configurations, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
---

## Parameter Configuration Classes

### PublicRuntimeSettings

You can update most of the parameter settings through the `PublicRuntimeSettings` class.

```java
import com.dynamsoft.dbr.PublicRuntimeSettings;
```

| Attribute | Type | Descriptions |
|---------- | ---- | ----------- |
| [`terminatePhase`](#terminatephase) | *int* | Sets the phase to stop the barcode reading algorithm. |
| [`timeout`](#timeout) | *int* | Set the maximum time spent on scanning one image (page). |
| [`maxAlgorithmThreadCount`](#maxalgorithmthreadcount) | *int* | Sets the number of threads the image processing algorithm will use to decode barcodes. |
| [`expectedBarcodesCount`](#expectedbarcodescount) | *int* | Sets the number of barcodes expected to be detected for each image. |
| [`barcodeFormatIds`](#barcodeformatids) | *int* | BarcodeFormat group 1. Read more in [`EnumBarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) |
| [`barcodeFormatIds_2`](#barcodeformatids_2) | *int* | BarcodeFormat group 2. Read more in [`EnumBarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2) |
| [`pdfRasterDPI`](#pdfrasterdpi) | *int* | Sets the output image resolution. |
| [`scaleDownThreshold`](#scaledownthreshold) | *int* | Sets the threshold for the image shrinking. |
| [`binarizationModes`](#binarizationmodes) | *int\[\]* | Sets the mode and priority for binarization. |
| [`localizationModes`](#localizationmodes) | *int\[\]* | Sets the mode and priority for localization algorithms. |
| [`furtherModes`](#furthermodes) | `FurtherModes` | Further modes settings. Please read more in [`FurtherModes`](FurtherModes.md) class. |
| [`deblurLevel`](#deblurlevel) | *int* | Sets the degree of blurriness of the barcode.
 |
| [`intermediateResultTypes`](#intermediateresulttypes) | *int* | Sets which types of intermediate result to be kept for further reference. |
| [`intermediateResultSavingMode`](#intermediateresultsavingmode) | *int* | Sets the mode for saving intermediate result. |
| [`resultCoordinateType`](#resultcoordinatetype) | *int* | Specifies the format for the coordinates returned. |
| [`textResultOrderModes`](#textresultordermodes) | *int\[\]* | Sets the mode and priority for the order of the text results returned. |
| [`returnBarcodeZoneClarity`](#returnbarcodezoneclarity) | *int* | Sets whether or not to return the clarity of the barcode zone. |
| [`region`](#region) | `RegionDefinition` | Sets the scan region. Please read more in [`RegionDefinition`](RegionDefinition.md) Class |
| [`minBarcodeTextLength`](#minbarcodetextlength) | *int* | Sets the range of barcode text length for barcodes search. |
| [`minResultConfidence`](#minresultconfidence) | *int* | The minimum confidence of the result. |
| [`scaleUpModes`](#scaleupmodes) | *int\[\]* | Sets the mode and priority to control the sampling methods of scale-up for linear barcode with small module sizes. |
| [`pdfReadingMode`](#pdfreadingmode) | *int* | Sets the way to detect barcodes from a PDF file when using the DecodeFile method. |
| [`deblurModes`](#deblurmodes) | *int\[\]* | Sets the mode and priority for deblurring. |
| [`barcodeZoneMinDistanceToImageBorders`](#barcodezonemindistancetoimageborders) | *int* | Sets the minimum distance (in pixels) between the barcode zone and image borders. |

```java
PublicRuntimeSettings runtimeSettings = barcodeReader.getRuntimeSettings();
// Make some settings here
// runtimeSettings.****** = ******
barcodeReader.updateRuntimeSettings(runtimeSettings);
```

### FurtherModes

`FurtherModes` is an extension of the `PublicRuntimeSettings` class. Through the `FurtherModes`, you can make advanced settings to process the image for barcode reading.

```java
import com.dynamsoft.dbr.FurtherModes;
```

| Attribute | Type | Descriptions |
|---------- | ---- | ----- |
| [`colourClusteringModes`](#colourclusteringmodes) | *int\[\]* | Sets the mode and priority for colour categorization. |
| [`colourConversionModes`](#colourconversionmodes) | *int\[\]* | Sets the mode and priority for converting a colour image to a grayscale image. |
| [`grayscaleTransformationModes`](#grayscaletransformationmodes) | *int\[\]* | Sets the mode and priority for the grayscale image conversion. |
| [`regionPredetectionModes`](#regionpredetectionmodes) | *int\[\]* | Sets the region pre-detection mode for barcodes search. |
| [`imagePreprocessingModes`](#imagepreprocessingmodes) | *int\[\]* | Sets the mode and priority for image preprocessing algorithms. |
| [`textureDetectionModes`](#texturedetectionmodes) | *int\[\]* | Sets the mode and priority for texture detection. |
| [`textFilterModes`](#textfiltermodes) | *int\[\]* | Sets the mode and priority for text filter. |
| [`textAssistedCorrectionMode`](#textassistedcorrectionmode) | *int* | Sets the mode of text assisted correction for barcode decoding. |
| [`dpmCodeReadingModes`](#dpmcodereadingmodes) | *int\[\]* | Sets the mode and priority for DPM code reading. |
| [`deformationResistingModes`](#deformationresistingmodes) | *int\[\]* | Sets the mode and priority for deformation resisting. |
| [`barcodeComplementModes`](#barcodecomplementmodes) | *int\[\]* | Sets the mode and priority to complement the missing parts in the barcode. |
| [`barcodeColourModes`](#barcodecolourmodes) | *int\[\]* | Sets the mode and priority for the barcode colour mode used to process the barcode zone. |
| [`accompanyingTextRecognitionModes`](#accompanyingtextrecognitionmodes) | *int\[\]* | Sets the mode and priority to recognize accompanying text. |

```java
FurtherModes furtherModes = runtimeSettings.furtherModes;
```

### RegionDefinition

```java
import com.dynamsoft.dbr.RegionDefinition;
```

| Attribute | Type | Descriptions |
|---------- | ---- | ------------ |
| [`regionTop`](#regiontop) | *int* | The top-most coordinate or percentage of the region. |
| [`regionLeft`](#regionleft) | *int* | The Left-most coordinate or percentage of the region. |
| [`regionRight`](#regionright) | *int* | The Right-most coordinate or percentage of the region. |
| [`regionBottom`](#regionbottom) | *int* | The Bottom-most coordinate or percentage of the region. |
| [`regionMeasuredByPercentage`](#regionmeasuredbypercentage) | *int* | Sets whether or not to use percentage to measure the region size. |

```java
RegionDefinition regionDefinition = runtimeSettings.region;
```

### FrameDecodingParameters

The parameters that helps you on frame decoding.

```java
import com.dynamsoft.dbr.FrameDecodingParameters;
```

| Attribute | Type | Descriptions |
|---------- | ---- | ------------ |
| [`maxQueueLength`](#maxqueuelength) | *int* | The maximum number of frames waiting for decoding. |
| [`maxResultQueueLength`](#maxresultqueuelength) | *int* | The maximum number of frames waiting results (text result/localization result) will be kept for further reference. |
| [`width`](#width) | *int* | The width of the frame image in pixels.  |
| [`height`](#height) | *int* | The height of the frame image in pixels. |
| [`stride`](#stride) | *int* | The stride (or scan width) of the frame image. |
| [`imagePixelFormat`](#imagepixelformat) | *int* | The image pixel format used in the image byte array. |
| [`region`](#region) | [`RegionDefinition`](RegionDefinition.md) | The region definition of the frame to calculate the internal indicator. |
| [`threshold`](#threshold) | *float* | The threshold used for filtering frames. |
| [`fps`](#fps) | *int* | The frequency of calling [`appendFrame`](../BarcodeReader/video.md#appendframe) per second. |
| [`autoFilter`](#autofilter) | *int* | Sets whether to filter frames automatically. |
| [`clarityCalculationMethod`](#claritycalculationmethod) | *int* | Sets the method used for calculating the clarity of the frames. |
| [`clarityFilterMode`](#clarityfiltermode) | *int* | Sets the mode used for filtering frames by calculated clarity. |

### DCESettingParameters

The parameters that helps you on configuring Dynamsoft Camera Enhancer in the Barcode Reader.

```java
import com.dynamsoft.dbr.DCESettingParameters;
```

| Attribute | type | Description |
|-----------|------|-------------|
| `cameraInstance` | *Object* | The Camera Enhancer instance |
|  `textResultCallback` | [`TextResultCallback`]({{site.android_api}}interface.html#textresultcallback) | Set text result callback. |
| `textResultCallback_UserData` | *Object*  | Transfer user data. |
| `intermediateResultCallback` | [`IntermediateResultCallback`]({{site.android_api}}interface.html#intermediateresultcallback) | Set intermediate result callback. |
| `IntermediateResultCallback_UserData` | *Object* | Transfer user data. |

```java
DCESettingParameters dceSettingParameters = new DCESettingParameters();
dceSettingParameters.cameraInstance = mCameraEnhancer;
dceSettingParameters.textResultCallback = mTextResultCallback;
reader.SetCameraEnhancerParam(dceSettingParameters);
```
