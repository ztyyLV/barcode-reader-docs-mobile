---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Video Methods
description: This page shows Video methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: startFrameDecoding, startFrameDecodingEx, appendFrame, stopFrameDecoding, getFrameDecodingParameters, setDBRErrorDelegate, setDBRTextResultDelegate, setDBRIntermediateResultDelegate, getLengthOfFrameQueue, video methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
---

# Video Decoding Methods

| Method               | Description |
|----------------------|-------------|
| [`setCameraEnhancer`](#setcameraenhancer) | Bind a Camera Enhancer instance to the Barcode Reader.  |
| [`startScanning`](#startscanning) | Start the barcode reading thread. |
| [`stopScanning`](#stopscanning) | Stop the barcode reading thread. |
| [`setDBRTextResultDelegate`](#setdbrtextresultdelegate) | Set callback function to process text results generated during frame decoding. |
| [`setDBRIntermediateResultDelegate`](#setdbrintermediateresultdelegate) | Set callback function to process intermediate results generated during frame decoding. |

---

## setCameraEnhancer

Bind a `Dynamsoft Camera Enhancer` instance to the Barcode Reader. `Dynamsoft Camera Enhancer` is designed for video streaming processing scenarios. It can help the Barcode Reader to acquire video frames continuously for video streaming barcode decoding.

```objc
- (void)setCameraEnhancer:(DynamsoftCameraEnhancer* _Nonnull)cameraInstance;
```

**Parameters**

`dce`: An instance of `Dynamsoft Camera Enhancer`.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
@property(nonatomic, strong) DynamsoftBarcodeReader *barcodeReader;
@property(nonatomic, strong) DynamsoftCameraEnhancer *dce;

[_barcodeReader setCameraEnhancer:_dce];
```
2. 
```swift
var dce:DynamsoftCameraEnhancer! = nil
var barcodeReader:DynamsoftBarcodeReader! = nil
barcodeReader.setCameraEnhancer(dce)
```

## startScanning

Start the video streaming barcode decoding thread. Please be sure that you have bound a Camera Enhancer to the barcode reader before you trigger `startScanning`.

```objc
-(void)startScanning;
```

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[_barcodeReader startScanning];
```
2. 
```swift
barcodeReader.startScanning()
```

## stopScanning

Stop the video streaming barcode decoding thread.

```objc
-(void)stopScanning;
```

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[_barcodeReader stopScanning];
```
2. 
```swift
barcodeReader.stopScanning()
```

## setDBRTextResultDelegate

Set callback function to process text results generated during frame decoding.

```objc
-(void)setDBRTextResultDelegate:(id _Nullable)textResultDelegate userData:(NSObject* _Nullable)userData;
```

**Parameters**

`[in] textResultDelegate`: Callback function.  
`[in] userData`: Customized arguments passed to your function.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader setDBRTextResultDelegate:self userData:nil];
```
2. 
```swift
barcodeReader.setDBRTextResultDelegate(self, userData:nil)
```

## setDBRIntermediateResultDelegate

Set callback function to process intermediate results generated during frame decoding.

```objc
-(void)setDBRIntermediateResultDelegate:(id _Nullable)intermediateResultDelegate userData:(NSObject* _Nullable)userData;
```

**Parameters**

`[in] intermediateResultDelegate`: Callback function.  
`[in] userData`: Customized arguments passed to your function.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
[barcodeReader setDBRIntermediateResultDelegate:self userData:nil];
```
2. 
```swift
barcodeReader.setDBRIntermediateResultDelegate(self, userData:nil)
```
