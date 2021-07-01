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

```java
import com.dynamsoft.dbr.PublicRuntimeSettings;
```

You can update most of the parameter settings through the `PublicRuntimeSettings` class.

```java
PublicRuntimeSettings runtimeSettings = barcodeReader.getRuntimeSettings();
runtimeSettings.barcodeFormatIds = 0;
runtimeSettings.region.regionLeft = 30;
runtimeSettings.region.regionTop = 15;
runtimeSettings.region.regionRight = 70;
runtimeSettings.region.regionBottom = 85;
```

### RegionDefinition

### FurtherModes

### FrameDecodingParameters

### DCESettingParameters

### Quadrilateral
