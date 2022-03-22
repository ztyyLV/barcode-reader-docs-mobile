---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - Advanced Usage
description: This is the Advanced Usage page of Dynamsoft Barcode Reader for iOS SDK.
keywords: Guide, iOS, Settings
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# Add Basic Settings

If you have followed the [Getting started](#user-guide.md), you may have managed to create a video streaming barcode reader project. In this article, you can learn about how to add basic runtime settings to your barcode reader project.

## Specify Barcode Formats

Specifying the barcode format is always the first step of barcode reader configuration. Be sure to confirm that the target barcode formats are included. Meanwhile, excluding the undesired barcodes will improve the processing efficiency. If you are not familiar with barcode format, the <a href="https://www.dynamsoft.com/barcode-types/barcode-types/" target="_blank">introduction of barcode formats</a> may help you understand it. Generally, the barcode format settings are updated via `PublicRuntimeSettings` class by specifying enumeration member of `BarcodeFormat` or `BarcodeFormat_2`.

```swift
// First step, get the instance of setting
// You can either get the instance from current settings or create a new instance.
let settings = try? barcodeReader.getRuntimeSettings()

// Second step, update the settings of barcodeFormatIds.
// There are two groups of barcode formats, BarcodeFormat and BarcodeFormat_2
// The Majority of common barcodes like oneD barcode and QR code are stored in the first group of barcode format.
// Some of the enumeration members are combined value of a group of barcodes like BF_ONED and BF_GS1_DATABAR
// Use "|" to enable multiple barcode formats at one time.
settings.barcodeFormatIds = EnumBarcodeFormat.ONED | EnumBarcodeFormat.QRCODE

// Update the settings.
try? barcodeReader.updateRuntimeSettings(settings!)
```

## Set Barcode Count

The `expectedBarcodeCount` is the parameter that controls the number of expected results of the recognized barcodes via barcode reader from a single image. The process will be stopped as soon as the count of successfully decoded barcodes reaches the expected amount.

There are some suggestions on how to set the `expectedBarcodeCount`:

- When your project is design for decoding **single** barcode, the recommended `expectedBarcodeCount` is **1**. This will sharply improve the processing speed.
- When there are **n** barcodes in a single image (**n** is a fixed number) and you'd like the barcode reader to decode **all of them**, the recommended `expectedBarcodeCount` is **n**.
- When the number of barcodes is unknown and you want to output **as many** barcode results as possible, you can set the `expectedBarcodeCount` to the **maximum possible count**.
- When the number of barcodes is unknown and you want to output **at least one** barcode result as soon as possible, you can set the `expectedBarcodeCount` to **0**. The barcode reader will try to decode at least one barcode from the image.

```swift
// Similar to the barcode format setting, you can update the barcode count setting via PublicRuntimeSettings.
let settings = try? barcodeReader.getRuntimeSettings()

// Set the expected barcode count.
settings.expectedBarcodesCount = 1

// You can update the barcode format settings together with the barcode count settings.
settings.barcodeFormatIds = EnumBarcodeFormat.ONED | EnumBarcodeFormat.QRCODE

// Update the settings.
try? barcodeReader.updateRuntimeSettings(settings!)
```

## Define a Scan Region

It is not always necessary to scan the whole image to get the barcode result. You can define a scan region for your barcode reader to narrow the searching region.

```swift
import DynamsoftCameraEnhancer

dceView = DCECameraView.init(frame: CGRect(x: 0, y: barHeight!, width: mainWidth, height: mainHeight - SafeAreaBottomHeight - barHeight!))
self.view.addSubview(dceView)
dce = DynamsoftCameraEnhancer.init(view: dceView)
let scanRegion = iRegionDefinition()
scanRegion.regionTop = 25
scanRegion.regionBottom = 75
scanRegion.regionLeft = 25
scanRegion.regionRight = 75
scanRegion.regionMeasuredByPercentage = 1
dce.setScanRegion(scanRegion, error:nil)
```

The above settings can meet the majority of usage scenarios. However, if the performance is still not satisfying, the following articles will help you on improving the performance.

- [Quick optimize performance](quick-performance-settings.md)

If you are facing license issues, the following pages might help you.

- [Licence Activation]({{ site.license_activation }})
