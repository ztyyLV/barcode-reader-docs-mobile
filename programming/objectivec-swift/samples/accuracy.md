---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - Accuracy-First Settings Samples
description: This is the Accuracy-First Settings Sample page of Dynamsoft Barcode Reader for iOS SDK.
keywords: iOS, samples, speed
needAutoGenerateSidebar: true
breadcrumbText: AccuracyFirstSettings
---

# AccuracyFirstSettings Sample

The Accuracy-First setting sample illustrates how to use DBR APIs to improve the barcode reading accuracy. Normally the barcode misreading is caused by decoding the terribly printed barcodes or blurry images. On this page, you can find the guides on how to deal with these issues to avoid misreading when using Dynamsoft Barcode Reader.

View the sample

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/v8.8.0/ios/Objective-C/Performance/AccuracyFirstSettingsObjC/" target="_blank">Speed-first Settings Sample (Objective-C)</a>
- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/v8.8.0/ios/Swift/Performance/AccuracyFirstSettingsSwift/" target="_blank">Speed-first Settings Sample (Swift)</a>

## Regular Accuracy Settings

Normally, the misreading is caused by the low-quality source. The low-quality source can be terribly printed barcodes or blurry images/frames. These low-quality barcodes can be recognized and localized. However, the barcode reader will take a lot of time to further process these barcodes and it is difficult to guarantee the accuracy of the results. It would be better to optimize the barcode source rather than try decoding on these low-quality barcodes.

### Frame Filter

Generally, the quality of input video streaming is determined by the performance of hardware. However, we still have solutions to deal with the blurry frames in the video streaming from the software end. <a href="https://www.dynamsoft.com/camera-enhancer/docs/introduction/?ver=latest" target="_blank">Dynamsoft Camera Enhancer (DCE)</a> is an SDK that provides video streaming pre-processing APIs which enable users to avoid decoding barcodes on low-quality frames. By enabling the frame filter feature of DCE, the sharpness of each frame will be detected and the low sharpness frames will be skipped in the barcode decoding process.

### Confidence

For every barcode result output by DBR, it has a confidence value. The higher the confidence is, the more possible it is to be correct. Currently, the barcode reader will always output the barcode result with the highest confidence and the confidence filter is enabled as well. The default value of the confidence filter is 30，which means the result with lower confidence will not be output.

**Related APIs**

[`MinResultConfidence`]({{ site.parameters_reference }}min-result-confidence.html)

### Multi-frame Confirmation

The multi-frame confirmation is a solution that eliminates misreading on oneD barcodes by double-checking the barcode results between multiple video frames before the results are output. Since this feature will halve the average reading speed, please enable this feature when the misreading is intolerable.

- Use [`enableResultVerification`]({{ site.oc_api }}primary-result.html#enableresultverification) to enable the result confirmation.

## Advanced Accuracy Settings

### Specify the Barcode Format

Barcode format is one of the most typical settings of a barcode reader. This will help you to improve the speed and accuracy of your barcode reading program by excluding the uninterested formats. You can update the barcode format settings in the struct/class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html) via API [`updateRuntimeSettings`]({{ site.oc_api }}primary-parameter-and-runtime-settings-basic.html#updateruntimesettings).

**Related APIs**

- Struct/class [`PublicRuntimeSettings`]({{ site.oc_api }}auxiliary-iPublicRuntimeSettings.html)
- API [`updateRuntimeSettings`]({{ site.oc_api }}primary-parameter-and-runtime-settings-basic.html#updateruntimesettings)
- Enum [`BarcodeFormat`]({{ site.enumerations }}format-enums.html#barcodeformat) and [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2)

### Skip Small-Sized Barcodes

It is always a harsh task for a generally configured barcode reader to recognize a small-sized barcode. The read rate of small-sized barcodes can be improved by configuring the mode parameters. However, the accuracy issue is still unresolved. As a result, when sacrificing the read rate on the small-sized barcodes is acceptable, you can make filters on the localized barcode to skip decoding on these non-interest barcodes. To make the small-sized barcode filter, **FormatSpecification** parameters [`BarcodeHeightRangeArray`]({{ site.parameters_reference }}barcode-height-range-array.html) and [`BarcodeWidthRangeArray`]({{ site.parameters_reference }}barcode-width-range-array.html) will help on defining the range of the barcode size. In addition, by configuring the above parameters, you can also filter out the incompatible shaped barcodes before decoding.

**Related APIs**

- Parameters [`BarcodeHeightRangeArray`]({{ site.parameters_reference }}barcode-height-range-array.html) and [`BarcodeWidthRangeArray`]({{ site.parameters_reference }}barcode-width-range-array.html).

### Exclude the Non-interest Results

For some scenarios, there might have some common features that can be applied to verify the correctness of the barcode result texts.

**The Text Length**

Set the minimum and maximum length of the barcode text to filter out the uninterested results. This feature can be configured via **FormatSpecification** parameter [`BarcodeTextLengthRangeArray`]({{ site.parameters_reference }}barcode-text-length-range-array.html).

**The Regular Expression Pattern**

Set the regular expression pattern of the barcode text to filter out the uninsterested results. This feature can be configured via **FormatSpecification** parameter [`BarcodeTextRegExPattern`]({{ site.parameters_reference }}barcode-text-regex-pattern.html).
