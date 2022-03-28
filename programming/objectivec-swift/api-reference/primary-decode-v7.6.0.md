---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - Decode Methods
description: This page shows Decode methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: decodeFileWithName, decodeImage, decodeBuffer, decodeBase64, decode methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
---

# Objective-C API Reference - Decode Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`decodeFileWithName`](#decodefilewithname) | Decode barcodes from a specified image file. |
  | [`decodeImage`](#decodeImage) | Decode barcodes from an image file in memory. |
  | [`decodeBuffer`](#decodeBuffer) | Decode barcodes from raw buffer. |
  | [`decodeBase64`](#decodeBase64) | Decode barcodes from a base64 encoded string. |
  
---

## decodeFileWithName

Decode barcodes from a specified image file.

```objc
- (NSArray<iTextResult*>* _Nullable)decodeFileWithName:(NSString* _Nonnull)name templateName:(NSString* _Nonnull)templateName error:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in] name` The local path of the file.  
`[in] templateName` The template name.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.  

**Return value**

All successfully decoded barcode results.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicense:@"t0260NwAAAHV***************"];
iTextResult *result;
NSError __autoreleasing * _Nullable error;
result = [barcodeReader decodeFileWithName:@"your file path" templateName:@"" error:&error];
```
2. 
```swift
let barcodeReader = DynamsoftBarcodeReader.init(license: "t0260NwAAAHV***************")
let error: NSError? = NSError()
let result = barcodeReader.decodeFileWithName(name:"your file path",templateName:"",error:&error)
```

&nbsp;

## decodeImage

Decode barcodes from an image file in memory.

```objc
- (NSArray<iTextResult*>* _Nullable)decodeImage:(UIImage* _Nonnull)image withTemplate:(NSString* _Nonnull)templateName error:(NSError* _Nullable * _Nullable)error;
```  

**Parameters**

`[in] image` The image file in memory.  
`[in] templateName` The template name.  
`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return value**

All successfully decoded barcode results.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicense:@"t0260NwAAAHV***************"];
iTextResult *result;
UIImage *image;
NSError __autoreleasing * _Nullable error;
result = [barcodeReader decodeImage:image withTemplate:@"" error:&error];
```
2. 
```swift
let barcodeReader = DynamsoftBarcodeReader.init(license: "t0260NwAAAHV***************")
let image: UIImage? = UIImage()
let error: NSError? = NSError()
let result = barcodeReader.decodeImage(image:image withTemplate:"" error:&error)
```

## decodeBuffer

Decode barcodes from the memory buffer containing image pixels in a defined format.

```objc
- (NSArray<iTextResult*>* _Nullable)decodeBuffer:(NSData* _Nonnull)buffer withWidth:(NSInteger)width height:(NSInteger)height stride:(NSInteger)stride format:(EnumImagePixelFormat)format templateName:(NSString* _Nonnull)templateName error:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in] buffer` The array of bytes that contain the image data.  
`[in] width` The width of the image in pixels.  
`[in] height` The height of the image in pixels.  
`[in] stride` The stride (or scan width) of the image.  
`[in] format` The image pixel format used in the image byte array.  
`[in] templateName` The template name.  
`[in, out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.  

**Return value**

All successfully decoded barcode results.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicense:@"t0260NwAAAHV***************"];
iTextResult *result;
NSData *bufferBytes;
NSInteger iWidth = 0;
NSInteger iHeight = 0;
NSInteger iStride = 0;
NSInteger format;
NSError __autoreleasing * _Nullable error;
result = [barcodeReader decodeBuffer:bufferBytes withWidth:iWidth height:iHeight stride:iStride format:format templateName:@"" error:&error];
```
2. 
```swift
let barcodeReader = DynamsoftBarcodeReader.init(license: "t0260NwAAAHV***************")
let error: NSError? = NSError()
let bufferBytes:Data?
let width = 0
let height = 0
let stride = 0
let format:Int
let result = try? barcodeReader.decodeBuffer(bufferBytes, width: width, height: height, stride: stride, format: format, templateName: "")
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

**Return value**

All successfully decoded barcode results.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicense:@"t0260NwAAAHV***************"];
iTextResult *result;
NSError __autoreleasing * _Nullable error;
result = [barcodeReader decodeBase64:@"file in base64 string" withTemplate:@"" error:&error];
```
2. 
```swift
let barcodeReader = DynamsoftBarcodeReader.init(license: "t0260NwAAAHV***************") 
let error: NSError? = NSError() 
let result = barcodeReader.decodeBase64(base64: file in base64 string, withTemplate: "", error: &error)
```

&nbsp;
