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
- How to add clickable torchlight button

## Preperations

UI configuring API are all included in DCECameraView class. All the UI configurations are implemented via the DCECameraView instance. You can use the following step to get prepared for UI configurations. These steps are all done if you have completed the steps in the [Getting started](user-guide.md) page.

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

The highlight overlays will be created and displayed on the UI automatically when you add the following code. You don't need to write any code for the location of overlays.

```java
cameraView.setOverlayVisible(true);
```

The stroke and fillin colour of the overlays are also available for setting.

```java
// The first value is stroke colour and the second one is fill in colour.
dceCameraView.setOverlayColour(0xff00ff00, 0x00000000);
```

## How to Add clickable Torchlight Button

In the cameraView, there is a build-in clickable torch button that can control the status of torchlight. You can add styles like location, size and image icon for the button.

```java

```
