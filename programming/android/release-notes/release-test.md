---
layout: default-layout
title: Dynamsoft Barcode Reader SDK - Release Notes
description: This is the release notes page of Dynamsoft Barcode Reader.
keywords: release notes
needGenerateH3Content: false
---

# Dynamsoft Barcode Reader v8.6.0 is Released!

## Highlights

{%- include release-notes/product-highlight-8.6.0.md -%}

## View Edition Changelogs

| [JavaScript](../programming/javascript/release-notes/js-8.md#860-08312021) | [C](../programming/c/release-notes/c-8.md#86-07152021) | [C++](../programming/cplusplus/release-notes/cpp-8.md#86-07152021) | [DotNet](../programming/dotnet/release-notes/dotnet-8.md#86-07152021) | **[Python](../programming/python/release-notes/python-8.md#86-07152021)** | **[Java](../programming/java/release-notes/java-8.md#86-07152021)** | **[Android](../programming/android/release-notes/android-8.md#86-07152021)** | **[iOS](../programming/objectivec-swift/release-notes/ios-8.md#86-07152021)** |

## Other 8.X Version Highlights

**8.4.0**

- Improved the recognition speeds when detecting dense QR Codes.
- Improved the performance of boundary identification for DataMatrix codes.
- Added a new `BinarizationModes` parameter `ThresholdCompensation` to replace the deprecated parameter `ThreshValueCoefficient`.

**8.2.0**

- Improved the performance on localizing and processing the Postal Codes

**8.1.2**

- Improved the recognition accuracy for GS1 Databar.

**8.1.0**

- Added support for MSI code (Modified Plessey).
- Improved the localization robustness for QR Code.
- Improved the localization for low-quality 1D barcodes.
- Improved the deblurring performance and recognition rate for DataMatrix.
- Improved the recognition rate for Aztec.

**8.0.0**

- Added a new license activation mechanism, license 2.0.
- Improved the localization speed for the ScanDirectly mode.
- Improved the localization accuracy for DataMatrix codes with a narrow quiet zone.
- Added a new parameter `DeblurModes` for users to apply different deblur algorithms for different scenarios.
- Added support for decoding `IntermediateResult`.
