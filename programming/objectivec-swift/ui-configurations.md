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

On this page, you will read:

- How to highlight the decoded barcodes
- How to display barcode result on the UI ()
- How to add clickable torchlight button

## Preparations

UI configuring API are all included in DCECameraView class. All the UI configurations are implemented via the DCECameraView instance. You can use the following step to get prepared for UI configurations. These steps are all done if you have completed the steps in the [Getting started](user-guide.md) page.

```objc
#import <DynamsoftCameraEnhancer/DynamsoftCameraEnhancer.h>
```

```objc
dceCameraView = [DCECameraView cameraWithFrame:self.view.bounds];
[self.view.addSubView:dceCameraView];
```

```swift
import DynamsoftCameraEnhancer
```

```swift
dceView = DCECameraView.init(frame: self.view.bounds)
self.view.addSubview(dceView)
```

## How to Highlight Decoded Barcodes

The highlight overlays will be created and displayed on the UI automatically when you add the following code. You don't need to write any code for the location of overlays.

```objc
[_dceView setOverlayVisible:true];
```

```swift
[_dceView setOverlayVisible:true];
```

The stroke and fill colour of the overlays are also available for setting.

```objc
UIColor* strokeColor = [UIColor colorWithRed:0.1 green:0.2 blue:0.3 alpha:0.5];
UIColor* fillColor = [UIColor colorWithRed:0.1 green:0.2 blue:0.3 alpha:0.5];
[_dceView setOverlayColour:strokeColor fill:fillColor];
```

```swift
let strokeColour = UIColor(red: 0.1, green: 0.2, blue: 0.3, alpha: 0.5)
let fillColour = UIColor(red: 0.1, green: 0.2, blue: 0.3, alpha: 0.5)
_dceView.setOverlayColour(strokeColour, fill: fillcolour)
```

## How to Add clickable Torchlight Button

In the `cameraView`, there is a build-in clickable torch button that can control the status of the torchlight. You can add styles like location, size and image icon for the button.

To display the torch button on the UI:

```objc
// If you don't add any styles for the button, the torch will be displayed on the top left corner of the screen.
dceCameraView.torchButtonVisible = true;
```

```swift
// If you don't add any styles for the button, the torch will be displayed on the top left corner of the screen.
dceCameraView.torchButtonVisible = true
```

The torch image can be set via UIImage. If you set the images to null, they will be set to the default value.

```objc
[dceCameraView setTorchButton:CGRectMake(100,100,50,50) torchOnImage:nil torchOffImage:nil];
```

```swift
dceCameraView.setTorchButton(CGRect(x:100, y:100, width:50, height:50), torchOn:nil, torchOffImage:nil)
```
