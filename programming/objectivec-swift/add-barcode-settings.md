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

If you have followed the guide in [Getting started](#user-guide.md), you have created a simplest video streaming barcode reader. On this page, you can learn about how to add basic settings for your barcode reader.

## Specify Barcode Formats

Before you start on this section, you can have a read of the <a href="https://www.dynamsoft.com/barcode-types/barcode-types/" target="_blank">introduction of barcode formats</a> to have a basic understanding on the barcodes. As one of the most basic barcode settings, specifying the barcode format will help you improve the speed and accuracy of your barcode reader.

Please do confirm all the targeting barcode formats in your requirements before you configure the barcode format settings. Generally, the barcode format settings are updated via `PublicRuntimeSettings` class by specifying enumeration member of `BarcodeFormat` or `BarcodeFormat_2`.

```swift
let error: NSError? = NSError()

// First step, get the instance of setting
// You can either get the instance from current settings or create a new instance.
let settings = try! barcodeReader.getRuntimeSettings()

// Second step, update the settings of barcodeFormatIds.
// There are two groups of barcode formats, BarcodeFormat and BarcodeFormat_2
// The Majority of common barcodes like oneD barcode and QR code are stored in the first group of barcode format.
// Some of the enumeration members are combined value of a group of barcodes like BF_ONED and BF_GS1_DATABAR
// Use "|" to enable multiple barcode formats at one time.
settings.barcodeFormatIds = EnumBarcodeFormat.BF_ONED | EnumBarcodeFormat.BF_QR_CODE

// Update the settings.
barcodeReader.update(settings, error: &error)
```

## Set Barcode Count

The `expectedBarcodeCount` is the parameter that controls how many barcodes you would like the barcode reader to recognize from a single image. There are some suggestions on how to set the `expectedBarcodeCount`:

- When the barcode reader is confirmed to focus on decoding single barcode, the recommended `expectedBarcodeCount` is 1. This will sharply improve the processing speed.
- When there are **n** barcodes in a single image (**n** is a fixed number) and you'd like the barcode reader to decode all of them, the recommended `expectedBarcodeCount` is **n**.
- Set the `expectedBarcodeCount` to 0 when the barcode count is uncertain. When the `expectedBarcodeCount` is set to 0, the barcode reader will try to decode at least one barcode from the image.

```swift
let error: NSError? = NSError()

// Similar to the barcode format setting, you can update the barcode count setting via PublicRuntimeSettings.
let settings = try! barcodeReader.getRuntimeSettings()

// Set the expected barcode count.
settings.expectedBarcodesCount = 1

// You can update the barcode format settings together with the barcode count settings.
settings.barcodeFormatIds = EnumBarcodeFormat.BF_ONED | EnumBarcodeFormat.BF_QR_CODE

// Update the settings.
barcodeReader.update(settings, error: &error)
```

## Set Scan Region

It is not always necessary to scan the whole image to get the barcode result. You can set a scan region for your barcode reader when scanning a small-sized barcode on an image.

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
dce.setScanRegion(scanRegion, error: &error)
```

The above settings are enough for the majority of usage scenarios. However, if the performance is still not satisfying, the following articles will help you on improving the performance.
