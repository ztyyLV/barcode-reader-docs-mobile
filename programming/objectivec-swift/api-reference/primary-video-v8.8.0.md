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
| [`startFrameDecoding`](#startframedecoding) | Starts a new thread to decode barcodes from the inner frame queue. |
| [`startFrameDecodingEx`](#startframedecodingex) | Starts a new thread to decode barcodes from the inner frame queue. |
| [`appendFrame`](#appendframe) | Appends a frame image buffer to the inner frame queue. |
| [`stopFrameDecoding`](#stopframedecoding) | Stops the frame decoding thread created by StartFrameDecoding. |
| [`getFrameDecodingParameters`](#getframedecodingparameters) | Initialize frame decoding parameter. |
| [`setDBRErrorDelegate`](#setdbrerrordelegate) | Set callback function to process errors generated during frame decoding. |
| [`setDBRTextResultDelegate`](#setdbrtextresultdelegate) | Set callback function to process text results generated during frame decoding. |
| [`setDBRIntermediateResultDelegate`](#setdbrintermediateresultdelegate) | Set callback function to process intermediate results generated during frame decoding. |
| [`getLengthOfFrameQueue`](#getlengthofframequeue) | Get length of current inner frame queue. |

---

## startFrameDecoding

Starts a new thread to decode barcodes from the inner frame queue.

```objc
-(void)startFrameDecoding:(NSInteger)maxQueueLength
    maxResultQueueLength:(NSInteger)maxResultQueueLength
    width:(NSInteger)width
    height:(NSInteger)height
    stride:(NSInteger)stride
    format:(EnumImagePixelFormat)format
    templateName:(NSString* _Nonnull)templateName
    error:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in] maxQueueLength` The max number of frames waiting for decoding.  
`[in] maxResultQueueLength` The max number of frames whose results (text result/localization result) will be kept.  
`[in] width` The width of the frame image in pixels.  
`[in] height` The height of the frame image in pixels.  
`[in] stride` The stride (or scan width) of the frame image.  
`[in] format` The image pixel format used in the image byte array.  
`[in] templateName` The template name.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
NSError __autoreleasing * _Nullable error;
[barcodeReader startFrameDecoding:2 maxResultQueueLength:10 width:1024 height:720 stride:720 format:EnumImagePixelFormatBinary templateName:@"" error:&error];
```
2. 
```swift
let error: NSError? = NSError()
barcodeReader.startFrameDecoding(maxQueueLength:2, maxResultQueueLength:10, width:1024, height:720, stride:720, format:EnumImagePixelFormat.Binary, templateName:"", error:&error)
```

## startFrameDecodingEx

Start a new thread to decode barcodes from the inner frame queue with specific frame decoding setting defined in [`iFrameDecodingParameters`](auxiliary-iFrameDecodingParameters.md) struct.

```objc
-(void)startFrameDecodingEx:(iFrameDecodingParameters* _Nullable) parameters
                templateName:(NSString* _Nonnull)templateName
                    error:(NSError* _Nullable __autoreleasing* _Nullable)error;
```

**Parameters**

`[in] parameters` The frame decoding parameters.  
`[in] templateName` The template name.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
NSError __autoreleasing * _Nullable error;
iFrameDecodingParameters *parameters = [barcodeReader getFrameDecodingParameters:nil];
parameters.maxQueueLength = 2;
parameters.maxResultQueueLength = 10;
parameters.width = 1024;
parameters.height = 720;
parameters.stride = 720;
parameters.imagePixelFormat = EnumImagePixelFormatBinary;
[barcodeReader startFrameDecodingEx:parameters templateName:@"" error:&error];
```
2. 
```swift
let error: NSError? = NSError()
let parameters = barcodeReader.getFrameDecodingParameters
parameters?.maxQueueLength = 2
parameters?.maxResultQueueLength = 10
parameters?.width = 1024
parameters?.height = 720
parameters?.stride = 720
parameters?.imagePixelFormat = EnumImagePixelFormat.Binary
barcodeReader.StartFrameDecodingEx(parameter: parameters!, templateName: "", error: &error)
```

## appendFrame

Appends a frame image buffer to the inner frame queue.

```objc
-(NSInteger)appendFrame:(NSData* _Nullable) bufferBytes;
```

**Parameters**

`[in] bufferBytes` The array of bytes which contain the image data.  

**Return Value**

Returns the ID of the appended frame.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
NSError __autoreleasing * _Nullable error;
[barcodeReader startFrameDecoding:2 maxResultQueueLength:10 width:1024 height:720 stride:720 format:EnumImagePixelFormatBinary templateName:@"" error:&error];
NSInteger frameId = [barcodeReader appendFrame:bufferBytes];
```
2. 
```swift
let error: NSError? = NSError()
barcodeReader.startFrameDecoding(maxQueueLength:2, maxResultQueueLength:10, width:1024, height:720, stride:720, format:EnumImagePixelFormat.Binary, templateName:"", error:&error)
let frameId = barcodeReader.appendFrame(bufferBytes:bufferBytes)
```

## stopFrameDecoding

Stops the frame decoding thread created by [`startFrameDecoding`](#startframedecoding) or [`startFrameDecodingEx`](#startframedecodingex).

```objc
-(void)stopFrameDecoding:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
NSError __autoreleasing * _Nullable error;
[barcodeReader startFrameDecoding:2 maxResultQueueLength:10 width:1024 height:720 stride:720 format:EnumImagePixelFormatBinary templateName:@"" error:&error];
[barcodeReader stopFrameDecoding:&error];
```
2. 
```swift
let error: NSError? = NSError()
barcodeReader.startFrameDecoding(maxQueueLength:2, maxResultQueueLength:10, width:1024, height:720, stride:720, format:EnumImagePixelFormat.Binary, templateName:"", error:nil)
barcodeReader.stopFrameDecoding(error:&error)
```

## getFrameDecodingParameters

Initialize frame decoding parameters with default values.

```objc
-(iFrameDecodingParameters*_Nullable)getFrameDecodingParameters:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

Returns frame decoding parameters.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
iFrameDecodingParameters *parameters = [barcodeReader getFrameDecodingParameters:nil];
```
2. 
```swift
let parameters = barcodeReader.getFrameDecodingParameters(error: nil)
```

## setDBRErrorDelegate

Sets callback function to process errors generated during frame decoding.

```objc
-(void)setDBRErrorDelegate:(id _Nullable)errorDelegate userData:(NSObject* _Nullable)userData;
```

**Parameters**

`[in] errorDelegate` Callback function.  
`[in] userData` Customized arguments passed to your function.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
[barcodeReader setDBRErrorDelegate:self userData:nil];
```
2. 
```swift
barcodeReader.setDBRErrorDelegate(errorDelegate:self, userData:nil)
```

## setDBRTextResultDelegate

Set callback function to process text results generated during frame decoding.

```objc
-(void)setDBRTextResultDelegate:(id _Nullable)textResultDelegate userData:(NSObject* _Nullable)userData;
```

**Parameters**

`[in] textResultDelegate` Callback function.  
`[in] userData`Customized arguments passed to your function.

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
barcodeReader.setDBRTextResultDelegate(textResultDelegate:self, userData:nil)
```

## setDBRIntermediateResultDelegate

Set callback function to process intermediate results generated during frame decoding.

```objc
-(void)setDBRIntermediateResultDelegate:(id _Nullable)intermediateResultDelegate userData:(NSObject* _Nullable)userData;
```

**Parameters**

`[in] intermediateResultDelegate` Callback function.  
`[in] userData` Customized arguments passed to your function.

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
barcodeReader.setDBRIntermediateResultDelegate(intermediateResultDelegate:self, userData:nil)
```

## getLengthOfFrameQueue

Get length of current inner frame queue.

```objc
-(NSInteger)getLengthOfFrameQueue;
```

**Return Value**

Returns the length of the inner frame queue.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
NSInteger length = [barcodeReader getLengthOfFrameQueue];
```
2. 
```swift
let length = barcodeReader.getLengthOfFrameQueue()
```
