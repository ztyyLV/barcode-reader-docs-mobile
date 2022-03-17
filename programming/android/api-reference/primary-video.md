---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Camera Methods
description: This page shows Camera methods of Dynamsoft Barcode Reader for Android SDK.
keywords: Camera methods, BarcodeReader, api reference, android
needAutoGenerateSidebar: true
noTitleIndex: true
pageStartVer: 8.6
---


# Video Decoding Methods

> Note:
>  
> - You have to include `CameraEnhancer` when using **Video Decoding Methods**.  
> - `CameraEnhancer` provide APIs that help you quickly deploy a camera module and capture video streaming for barcode decoding.  
> - Through **Video Decoding Methods** you can control whether to start video streaming barcode decoding and get the barcode results.  
> - Be sure that your `BarcodeReader` version is **8.9.0+** and `CameraEnhancer` is **2.1.0+** when using the methods on this page.

| Method | Description |
|--------|-------------|
| [`setCameraEnhancer`](#setcameraenhancer) | Bind a Camera Enhancer instance to the Barcode Reader.  |
| [`startScanning`](#startscanning) | Start the barcode reading thread. |
| [`stopScanning`](#stopscanning) | Stop the barcode reading thread. |
| [`setTextResultListener`](#settextresultlistener) | Set callback interface to process text results generated during frame decoding. |
| [`setIntermediateResultListener`](#setintermediateresultlistener) | Set callback interface to process intermediate results generated during frame decoding. |

---

## setCameraEnhancer

Bind a `Dynamsoft Camera Enhancer` instance to the Barcode Reader. `Dynamsoft Camera Enhancer` is designed for video streaming processing scenarios. It can help the Barcode Reader to acquire video frames continuously for video streaming barcode decoding.

```java
void setCameraEnhancer(CameraEnhancer mCameraEnhancer)
```

**Parameters**

`mCameraEnhancer`: An instance of `Dynamsoft Camera Enhancer`.

**Code Snippet**

This code snippet displays a complete code on how to add CameraEnhancer to your project and start to use Video Decoding Methods to decode and get barcode results from the video streaming.

```java
BarcodeReader reader;
CameraEnhancer mCameraEnhancer;
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    // Be sure that you have added a cameraView in the layout file.
    DCECameraView cameraView = findViewById(R.id.cameraView);
    try {
        // Create an instance of Dynamsoft Barcode Reader.
        reader = new BarcodeReader();
    } catch (BarcodeReaderException e) {
        e.printStackTrace();
    }
    mCameraEnhancer = new CameraEnhancer(MainActivity.this);
    mCameraEnhancer.setCameraView(cameraView);

    // Bind the Camera Enhancer instance to the Barcode Reader instance.
    reader.setCameraEnhancer(mCameraEnhancer);

    // Result callback configurations
    TextResultListener mTextResultListener = new TextResultListener() {
        // Obtain the recognized barcode results and display.
        @Override
        public void textResultCallback(int id, ImageData imageData, TextResult[] textResults) {
            // Add your code to execute when barcode results are returned.
        }
    };
    reader.setTextResultListener(mTextResultListener);
}
@Override
public void onResume() {
    // Open the camera and start video barcode reading
    try {
        mCameraEnhancer.open();
    } catch (CameraEnhancerException e) {
        e.printStackTrace();
    }
    reader.startScanning();
    super.onResume();
}

@Override
public void onPause() {
    // Stop video barcode reading
    try {
        mCameraEnhancer.close();
    } catch (CameraEnhancerException e) {
        e.printStackTrace();
    }
    reader.stopScanning();
    super.onPause();
}
```

## startScanning

Start the video streaming barcode decoding thread. Please be sure that you have bound a Camera Enhancer to the barcode reader before you trigger `startScanning`.

```java
void startScanning()
```

**Code Snippet**

You can view the complete code snippet in [`setCameraEnhancer`](#setcameraenhancer).

```java
BarcodeReader reader = new BarcodeReader();
reader.startScanning();
```

## stopScanning

You can view the complete code snippet in [`setCameraEnhancer`](#setcameraenhancer).

```java
void stopScanning()
```

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
reader.stopScanning();
```

## setTextResultListener

Set a callback interface to process text results generated during frame decoding.

```java
void setTextResultListener(TextResultCallback textResultCallback)
```

**Parameters**

`textResultCallback`: Callback interface.

**Code Snippet**

You can view the complete code snippet in [`setCameraEnhancer`](#setcameraenhancer).

```java
BarcodeReader reader = new BarcodeReader();
reader.setTextResultListener(new TextResultListener() {
    @Override
    public void textResultCallback(int frameId, ImageData imageData, TextResult[] results) {
        //TODO add your code for using text results
    }
});
```

## setIntermediateResultListener

Set a callback interface to process intermediate results generated during frame decoding.

```java
void setIntermediateResultListener(IntermediateResultCallback intermediateResultCallback}
```

**Parameters**

`intermediateResultCallback`: Callback interface.

**Code Snippet**

The usage of `intermediateResultListener` is similar to the `textResultListener`. You can view detailed code snippet in [`setCameraEnhancer`](#setcameraenhancer) and replace the `textResultListener` code with the `intermediateResultListener` code.

```java
BarcodeReader reader = new BarcodeReader();
PublicRuntimeSettings settings = reader.getRuntimeSettings();
// You can set intermediateResult type when using intermediateResultListener
settings.intermediateResultTypes = EnumIntermediateResultType.IRT_ORIGINAL_IMAGE | EnumIntermediateResultType.IRT_COLOUR_CLUSTERED_IMAGE | EnumIntermediateResultType.IRT_COLOUR_CONVERTED_GRAYSCALE_IMAGE;
reader.updateRuntimeSettings(settings);
reader.setIntermediateResultListener(new IntermediateResultCallback() {
    @Override
    public void intermediateResultCallback(int frameId, int imageData, IntermediateResult[] results) {
        //TODO add your code for using intermediate results
    }
});
```
