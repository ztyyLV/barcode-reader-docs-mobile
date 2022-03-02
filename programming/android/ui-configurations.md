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

```java
import com.dynamsoft.dce.DCECameraView;
```

```xml
<com.dynamsoft.dce.DCECameraView
    android:id="@+id/cameraView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:layout_editor_absoluteX="25dp"
    tools:layout_editor_absoluteY="0dp" />
```

```java
DCECameraView cameraView = findViewById(R.id.cameraView);
```

## How to Highlight Decoded Barcodes

By adding the following codes, the decoded barcodes will be automatically highlighted with a real-time overlay.

```java
cameraView.setOverlayVisible(true);
```

The stroke and fill colour of the overlays are also available for setting.

```java
// The first value is stroke colour and the second one is fill in colour.
cameraView.setOverlayColour(0xff00ff00, 0x00000000);
```

## How to Add clickable Torchlight Button

In the `cameraView`, there is a build-in clickable torch button that can control the status of the torchlight. By invoking APIs, you can control the parameters such as position, size and icon of the button.

To display the torch button on the UI:

```java
// If you don't add any styles for the button, the torch will be displayed on the top left corner of the screen.
cameraView.setTorchButtonVisible(true);
```

To add styles for the button:

```java
cameraView.setTorchButton(new Point(100,100),50,50,getDrawable(R.drawable.torch_on),getDrawable(R.drawable.torch_off));
```

If you set the position or images to null, they will be set to the default value.

```java
cameraView.setTorchButton(null,50,50,null,null);
```
