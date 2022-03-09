---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Decode Methods
description: This page shows Decode methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: decodeFileWithName, decodeImage, decodeBuffer, decodeBase64, decode methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
needGenerateH3Content: false
---


# Decode Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`decodeBuffer`](#decodebuffer) | Decode barcodes from raw buffer. |
  | [`decodeFileWithName`](#decodefilewithname) | Decode barcodes from a specified image file. |
  | [`decode`](#decode) | Decode barcodes from an image file in memory. |
  | [`decodeBase64`](#decodebase64) | Decode barcodes from a base64 encoded string. |
  | [`createIntermediateResult`](decode.md#createintermediateresult) | Inits an intermediateResult struct with default values. |
  | [`decodeIntermediateResults`](#decodeintermediateresults) | Decodes barcode from intermediate results. |
  
---

## decodeBuffer

Decode barcodes from the memory buffer containing image pixels in a defined format.

```objc
- (NSArray<iTextResult*>* _Nullable)decodeBuffer:(NSData* _Nonnull)buffer withWidth:(NSInteger)width height:(NSInteger)height stride:(NSInteger)stride format:(EnumImagePixelFormat)format templateName:(NSString* _Nonnull)templateName error:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in] buffer` The array of bytes which contain the image data.  
`[in] width` The width of the image in pixels.  
`[in] height` The height of the image in pixels.  
`[in] stride` The stride is measured by the `byte` length of each line in the `buffer`.  
`[in] format` The image pixel format used in the image byte array.  
`[in] templateName` For general usage, please set an empty string for the `templateName`. For further usage, please read the article of [parameter configuration]({{site.parameters}}scenario-settings/how-to-set-parameters.html).  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

```json
// Template name example.
// The "IP1" is the template name of this template. 
{
  "Version": "3.0",
  "ImageParameter": {                   
    "Name": "IP1",
    "Description": "This is an imageParameter", 
    "BarcodeFormatIds": ["BF_ALL"]
  }
}
```

**Return Value**

All successfully decoded barcode text results.

### Get ImageData from DCEFrame

If you have imported **DynamsoftCameraEnhancer.framework**, you can get video frames from the `frameOutputCallback`. DCEFrame object contains all required parameters of decodeBuffer method.

**Code Snippet**

Objective-C:

```objc
[_dce addListener:self];
//Get frames in callback methods.
- (void)frameOutPutCallback:(DCEFrame *)frame timeStamp:(NSTimeInterval)timeStamp{
    NSArray<iTextResult*>* results = [barcodeReader decodeBuffer:frame.imageData withWidth:frame.width height:frame.height stride:frame.stride format:frame.pixelFormat templateName:@"" error:nil];
}
```

Swift:

```swift
func frameOutPutCallback(_ frame: DCEFrame, timeStamp: TimeInterval){
  let result = try! barcodeReader.decodeBuffer(frame.imageData, withWidth: frame.width, height: frame.height, stride: frame.stride, format: EnumImagePixelFormat(rawValue: frame.pixelFormat) ?? EnumImagePixelFormat.ARGB_8888, templateName: "")
}
```

### Get ImageData from CaptureOutput

If you are acquiring video frames from `captureOutput` callback, you can use the following code to extract the required parameters from `sampleBuffer`.

**Code Snippet**

Objective-C:

```objc
- (void)captureOutput:(AVCaptureOutput *)captureOutput didOutputSampleBuffer:(CMSampleBufferRef)sampleBuffer fromConnection:(AVCaptureConnection *)connection;
{
  // Extract image data from sampleBuffer.
  CVImageBufferRef imageBuffer = CMSampleBufferGetImageBuffer(sampleBuffer);
  CVPixelBufferLockBaseAddress(imageBuffer, kCVPixelBufferLock_ReadOnly);
  int bufferSize = (int)CVPixelBufferGetDataSize(imageBuffer);
  int imgWidth = (int)CVPixelBufferGetWidth(imageBuffer);
  int imgHeight = (int)CVPixelBufferGetHeight(imageBuffer);
  size_t bpr = CVPixelBufferGetBytesPerRow(imageBuffer);
  void *baseAddress = CVPixelBufferGetBaseAddress(imageBuffer);
  CVPixelBufferUnlockBaseAddress(imageBuffer, kCVPixelBufferLock_ReadOnly);
  NSData * buffer = [NSData dataWithBytes:baseAddress length:bufferSize];
  startRecognitionDate = [NSDate date];
  NSArray* results = [m_barcodeReader decodeBuffer:buffer withWidth:imgWidth height:imgHeight stride:bpr format: EnumImagePixelFormatARGB_8888 templateName:@"" error:nil];
}
```

Swift:

```swift
func captureOutput(_ output: AVCaptureOutput, didOutput sampleBuffer: CMSampleBuffer, from connection: AVCaptureConnection){
  let imageBuffer:CVImageBuffer = CMSampleBufferGetImageBuffer(sampleBuffer)!
  CVPixelBufferLockBaseAddress(imageBuffer, .readOnly)
  let baseAddress = CVPixelBufferGetBaseAddress(imageBuffer)
  let bufferSize = CVPixelBufferGetDataSize(imageBuffer)
  let width = CVPixelBufferGetWidth(imageBuffer)
  let height = CVPixelBufferGetHeight(imageBuffer)
  let bpr = CVPixelBufferGetBytesPerRow(imageBuffer)
  CVPixelBufferUnlockBaseAddress(imageBuffer, .readOnly)
  startRecognitionDate = NSDate()
  let buffer = Data(bytes: baseAddress!, count: bufferSize)
  guard let results = try! barcodeReader.decodeBuffer(buffer, withWidth: width, height: height, stride: bpr, format: .ARGB_8888, templateName: "")
}
```

## decodeFileWithName

Decode barcodes from a specified image file.

```objc
- (NSArray<iTextResult*>* _Nullable)decodeFileWithName:(NSString* _Nonnull)name templateName:(NSString* _Nonnull)templateName error:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in] name` The local path of the file. It supports BMP, TIFF, JPG, PNG and PDF files.  
`[in] templateName` The template name.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

All successfully decoded barcode text results.

**Code Snippet**

Objective-C:

```objc
NSArray<iTextResult*>* result = [barcodeReader decodeFileWithName:@"your file path" templateName:@"" error:&error];
```

Swift:

```Swift
let error: NSError? = NSError()
let result = try! barcodeReader.decodeFile(withName: "your file path",templateName:"")
```

## decode

Decode barcodes from an image file in memory.

```objc
- (NSArray<iTextResult*>* _Nullable)decode:(UIImage* _Nonnull)image withTemplate:(NSString* _Nonnull)templateName error:(NSError* _Nullable * _Nullable)error;
```  

**Parameters**

`[in] image` The image file in memory.  
`[in] templateName` The template name.  
`[in, out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

All successfully decoded barcode text results.

**Code Snippet**

Objective-C:

```objc
UIImage *image = [[UIImage alloc] init];
NSError __autoreleasing * _Nullable error;
NSArray<iTextResult*>* result = [barcodeReader decodeImage:image withTemplate:@"" error:&error];
```

Swift:

```Swift
let image: UIImage? = UIImage()
let error: NSError? = NSError()
let result = try! barcodeReader.decodeImage(image withTemplate:"")
```

## decodeBase64

Decode barcodes from an image file encoded as a base64 string.

```objc
DBR_API int DBR_DecodeBase64String (void* barcodeReader, const char* pBase64String, const char* pTemplateName)
```

**Parameters**

`[in] base64` A base64 encoded string that represents an image.  
`[in] templateName` The template name.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

All successfully decoded barcode text results.

**Code Snippet**

Objective-C:

```objc
NSError __autoreleasing * _Nullable error;
NSArray<iTextResult*>* result = [barcodeReader decodeBase64:@"file in base64 string" withTemplate:@"" error:&error];
```

Swift:

```Swift
let error: NSError? = NSError() 
let result = try! barcodeReader.decodeBase64("file in base64 string", withTemplate: "")
```

## createIntermediateResult

Inits an intermediateResult struct with default values.

```objc
- (iIntermediateResult* _Nullable)createIntermediateResult:(EnumIntermediateResultType)type error:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in] type` The type of the intermediate result to init.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

An intermediateResult struct with default values.

**Code Snippet**

Objective-C:

```objc
NSError __autoreleasing * _Nullable error;
iIntermediateResult *irResult;
irResult = [barcodeReader createIntermediateResult:EnumIntermediateResultTypeOriginalImage error:&error];
```

Swift:

```Swift
var error:NSError? = NSError()
var irResult:iIntermediateResult!
irResult = try! barcodeReader.createIntermediateResult(EnumIntermediateResultType(rawValue: EnumIntermediateResultType.originalImage.rawValue)!)
```

## decodeIntermediateResults

Decodes barcode from intermediate results.

```objc
- (NSArray<iTextResult*>* _Nullable)decodeIntermediateResults:(NSArray<iIntermediateResult*>* _Nullable)array templateName:(NSString* _Nonnull)templateName error:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in] array` The intermediate result array for decoding.  
`[in] templateName` The template name.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

All successfully decoded barcode text results.

**Code Snippet**

Objective-C:

```objc
NSError __autoreleasing * _Nullable error;
[barcodeReader getRuntimeSettings:&error];
settings.intermediateResultTypes = EnumIntermediateResultTypeOriginalImage | EnumIntermediateResultTypeTypedBarcodeZone;
settings.intermediateResultSavingMode = EnumIntermediateResultSavingModeMemory;
[barcodeReader updateRuntimeSettings:settings error:&error];
NSArray<iTextResult*>* resultByFile = [barcodeReader decodeFileWithName:@"your file path" templateName:@"" error:&error];
NSArray<iIntermediateResult*>* array = [barcodeReader getIntermediateResult:&error];
NSArray<iTextResult*>* result = [barcodeReader decodeIntermediateResults:array withTemplate:@"" error:&error];
```

Swift:

```Swift
let result:[iTextResult]?
let settings = try! barcodeReader.getRuntimeSettings()
settings.intermediateResultTypes = EnumIntermediateResultType.originalImage.rawValue | EnumIntermediateResultType.typedBarcodeZone.rawValue
settings.intermediateResultSavingMode = .memory
barcodeReader.update(settings, nil)
result = try! barcodeReader.decodeFile(withName: "your file path", templateName: "")
let intermediateResult = try! barcodeReader.getIntermediateResult()
result = try! barcodeReader.decode(array, withTemplate: "")
```
