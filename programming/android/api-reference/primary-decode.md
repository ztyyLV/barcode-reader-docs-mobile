---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - BarcodeReader Decode Methods
description: This page shows BarcodeReader Decode methods of Dynamsoft Barcode Reader for Android SDK.
keywords: decodeFile, decodeFileInMemory, decodeBuffer, decodeBase64String, decodeBufferedImage, decode methods, BarcodeReader, api reference, android
needAutoGenerateSidebar: true
noTitleIndex: true
---


# Decode Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`decodeFile`](#decodefile) | Decode barcodes from a specified image file. |
  | [`decodeFileInMemory`](#decodefileinmemory) | Decode barcodes from an image file in memory. |
  | [`decodeBuffer`](#decodebuffer) | Decode barcodes from raw buffer. |
  | [`decodeBase64String`](#decodebase64string) | Decode barcodes from a base64 encoded string. |
  | [`decodeBufferedImage`](#decodeBufferedImage) | Decodes barcode from a buffered imag (bitmap). |
  | [`initIntermediateResult`](#initintermediateresult) | Inits an intermediateResult struct with default values. |
  | [`decodeIntermediateResults`](#decodeintermediateresults) | Decodes barcode from intermediate results. |
  
  ---

## decodeFile

Decode barcodes from a specified image file.

```java
TextResult[] decodeFile(String fileFullPath, String templateName) throws BarcodeReaderException
```

**Parameters**

`fileFullPath`: A string defining the file path. It supports BMP, TIFF, JPG, PNG and PDF files.  
`templateName`: The template name. When you upload settings from JSON String or file, you can add a template name for each group of settings. The template settings will be recorded even if they are overwritten. When using Dynamsoft decode methods, you can specify a template name to apply a previously set template. Otherwise, the currently activated template will take over the barcode decoding.

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

All successfully decoded barcode results.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
/*Init DBR license before decoding*/
/*Read external storage permission is required when decoding from a file*/
TextResult[] result = reader.decodeFile(Environment.getExternalStorageDirectory().toString()+"your file path", "IP1");
reader.destroy();
```

## decodeFileInMemory

Decode barcodes from an image file in memory.

### fileBytes

```java
TextResult[] decodeFileInMemory(byte[] fileBytes, String templateName) throws BarcodeReaderException
```

**Parameters**

`fileBytes`: The image file bytes in memory.  
`templateName`: The template name.

**Return Value**

All successfully decoded barcode results.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
/*Init DBR license before decoding
get bufferBytes from other component*/
TextResult[] result = reader.decodeFileInMemory(bufferBytes, "");
reader.destroy();
```

### fileStream

```java
TextResult [] decodeFileInMemory(InputStream fileStream, String templateName) throws BarcodeReaderException, IOException
```

**Parameters**

`fileStream`: The image file bytes in memory.  
`templateName`: The template name.

**Return Value**

All successfully decoded barcode results.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md), IOException

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
/*Init DBR license before decoding
get bufferBytes from other component*/
TextResult[] result = reader.decodeFileInMemory(fis, "");
reader.destroy();
```

## decodeBuffer

Decode barcodes from the memory buffer containing image pixels in defined format.

```java
TextResult[] decodeBuffer(byte[] buffer, int width, int height, int stride, int enumImagePixelFormat, String templateName) throws BarcodeReaderException
```

**Parameters**

`buffer`: The array of bytes which contain the image data.  
`Width`: The width of the image in pixels.  
`Height`: The height of the image in pixels.  
`Stride`: The stride (or scan width) of the image.  
`format`: The image pixel format used in the image byte array.  
`templateName`: The template name.

**Return Value**

All successfully decoded barcode results.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

There are several approaches for you to get a buffered image.

### Get Buffered Images from DCEFrame

You can import CameraEnhancer to acquire buffered video frames from `frameOutputCallback` or `videoBuffer` of DCE.

**Code Snippet**

```java
/*You can get frames from frame output call back if you import dynamsoft camera enhancer package.*/
/*You can get all the required parameters of decodeBuffer from DCEFrame.*/
import com.dynamsoft.dce.CameraEnhancer;

BarcodeReader reader = new BarcodeReader();
mCameraEnhancer.addListener(new DCEFrameListener() {
  @Override
  public void frameOutputCallback(DCEFrame dceFrame, long l) {
    try {
      TextResult[] results = reader.decodeBuffer(dceFrame.getImageData(),dceFrame.getWidth(),dceFrame.getHeight(),dceFrame.getStrides()[0],dceFrame.getPixelFormat(),"Put a template name here if you want to specify a previously set runtime setting template.");
    } catch (BarcodeReaderException e) {
      e.printStackTrace();
    }
  }
});
```

### Get Buffered Images from ImageReader

When you are using Android Camera2, you can get video frames from ImageReader.

**Code Snippet**

```java
previewReader.setOnImageAvailableListener(new ImageReader.OnImageAvailableListener() {
  @Override
  public void onImageAvailable(ImageReader reader) {
    Image mImage = reader.acquireLatestImage();
    ByteBuffer bufferY = mImage.getPlanes()[0].getBuffer();
    int strideY = mImage.getPlanes()[0].getRowStride() / mImage.getPlanes()[0].getPixelStride();
    ByteBuffer bufferU = mImage.getPlanes()[1].getBuffer();
    int strideU = mImage.getPlanes()[1].getRowStride() / mImage.getPlanes()[1].getPixelStride();
    ByteBuffer bufferV = mImage.getPlanes()[2].getBuffer();
    int strideV = mImage.getPlanes()[2].getRowStride() / mImage.getPlanes()[2].getPixelStride();
    int padingY = mImage.getPlanes()[0].getRowStride() - mImage.getWidth();
    int padingU = mImage.getPlanes()[1].getRowStride() - mImage.getWidth();
    byte[] newData = new byte[bufferY.limit()];
    newData = new byte[bufferY.limit() + bufferU.limit() + 1 + padingY + padingU];
    bufferV.get(newData, bufferY.limit() + padingY, 1);
    bufferU.get(newData, bufferY.limit() + padingY + 1, bufferU.limit());
    bufferY.get(newData, 0, bufferY.limit());
    int[] strides = new int[]{strideY, strideU, strideV};

    try {
      TextResult[] results = reader.decodeBuffer(newData, strideY, mImage.getHeight(), strideY, 3, "Put a template name here if you want to specify a previously set runtime setting template.");
    } catch (BarcodeReaderException e) {
      e.printStackTrace();
    }
  }
},handler);
```

## decodeBase64String

Decode barcode from an image file encoded as a base64 string.

```java
TextResult[] decodeBase64String(String base64, String templateName) throws BarcodeReaderException
```

**Parameters**

`base64`: A base64 encoded string that represents an image.  
`templateName`: The template name.

**Return Value**

All successfully decoded barcode results.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
/*Init DBR license before decoding*/
TextResult[] result = reader.decodeBase64String("file in base64 string", "");
reader.destroy();
```

## decodeBufferedImage

Decodes barcode from a buffered image (bitmap).

```java
TextResult[] decodeBufferedImage(Bitmap image, String templateName) throws BarcodeReaderException
```

**Parameters**

`image`: The image to be decoded.  
`templateName`: The template name.

**Return Value**

All successfully decoded barcode results.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md), IOException

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
/*Init DBR license before decoding*/
/*get BufferedImage input from other component*/
TextResult[] result = reader.decodeBufferedImage(input, "");
reader.destroy();
```

## initIntermediateResult

Inits an intermediateResult struct with default values.

```java
IntermediateResult initIntermediateResults(int resultType) throws BarcodeReaderException
```

**Parameters**

`resultType`: The type of the intermediate result to init.

**Return Value**

An intermediateResult struct with default values.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
/*Init DBR license before decoding*/
IntermediateResult imResult = reader.initIntermediateResult(EnumIntermediateResultType.IRT_ORIGINAL_IMAGE);
```

## decodeIntermediateResults

Decodes barcode from intermediate results.

```java
TextResult[] decodeIntermediateResults(IntermediateResult[] results, String templateName) throws BarcodeReaderException
```

**Parameters**

`results`: An array of intermediate result.  
`templateName`: The template name.

**Return Value**

All barcode text results decoded successfully.

**Exceptions**

[`BarcodeReaderException`](auxiliary-BarcodeReaderException.md)

**Code Snippet**

```java
BarcodeReader reader = new BarcodeReader();
/*Init DBR license before decoding*/
PublicRuntimeSettings settings = reader.getRuntimeSettings();
settings.intermediateResultTypes = EnumIntermediateResultType.IRT_ORIGINAL_IMAGE;
reader.updateRuntimeSettings(settings);
reader.decodeFile("your file path", "");
IntermediateResult[] irtResult = reader.getIntermediateResults();
TextResult[] result = reader.decodeIntermediateResults(irtResult, "");
```
