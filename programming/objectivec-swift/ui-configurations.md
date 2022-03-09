---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - UI Configurations
description: This is the UI Configurations of Dynamsoft Barcode Reader for Android SDK.
keywords: UI Configurations, Android
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---

# UI Configurations

In this article, you will learn:

- How to highlight the decoded barcodes
- How to add clickable torchlight button

## Preparations

UI configuring APIs are all included in DCECameraView class. All the UI configurations are implemented via the DCECameraView instance. You can use the following steps to get prepared for UI configurations. These steps are also mentioned in the [Getting started](user-guide.md).
<!--
Objective-C:

```objc
#import <DynamsoftCameraEnhancer/DynamsoftCameraEnhancer.h>
```

```objc
dceCameraView = [DCECameraView cameraWithFrame:self.view.bounds];
[self.view.addSubView:dceCameraView];
```

Swift:
-->

```swift
import DynamsoftCameraEnhancer
```

```swift
dceCameraView = DCECameraView.init(frame: self.view.bounds)
self.view.addSubview(dceCameraView)
```

## How to Highlight Decoded Barcodes

By adding the following codes, the decoded barcodes will be automatically highlighted with a real-time overlay.
<!--
Objective-C:

```objc
[dceCameraView setOverlayVisible:true];
```

Swift:
-->

```swift
dceCameraView.setOverlayVisible = true
```

The stroke and fill colour of the overlays are also available for setting.
<!--
Objective-C:

```objc
UIColor* strokeColor = [UIColor colorWithRed:0.1 green:0.2 blue:0.3 alpha:0.5];
UIColor* fillColor = [UIColor colorWithRed:0.1 green:0.2 blue:0.3 alpha:0.5];
[dceCameraView setOverlayColour:strokeColor fill:fillColor];
```

Swift:
-->

```swift
let strokeColour = UIColor(red: 0.1, green: 0.2, blue: 0.3, alpha: 0.5)
let fillColour = UIColor(red: 0.1, green: 0.2, blue: 0.3, alpha: 0.5)
dceCameraView.setOverlayColour(strokeColour, fill: fillcolour)
```

## How to Add clickable Torchlight Button

In the `cameraView`, there is a build-in clickable torch button that can control the status of the torchlight. By invoking APIs, you can control the parameters such as position, size and icon of the button.

To display the torch button on the UI:
<!--
Objective-C:

```objc
// If you don't add any styles for the button, the torch will be displayed on the top left corner of the screen.
[dceCameraView torchButtonVisible:true];
```

Swift:
-->

```swift
// If you don't add any styles for the button, the torch will be displayed on the top left corner of the screen.
dceCameraView.torchButtonVisible = true
```

If you set the position or images to nil value, they will be set to the default value.

Objective-C:
<!--
```objc
[dceCameraView setTorchButton:CGRectMake(100,100,50,50) torchOnImage:nil torchOffImage:nil];
```

Swift:
-->

```swift
dceCameraView.setTorchButton(CGRect(x:100, y:100, width:50, height:50), torchOn:nil, torchOffImage:nil)
```
