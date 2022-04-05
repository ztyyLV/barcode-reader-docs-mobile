---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - How to use the Barcode Reader without the Camera Enhancer
description: This is the Advanced Usage page of Dynamsoft Barcode Reader for Android SDK.
keywords: iOS, sample, Android, camera
needAutoGenerateSidebar: true
breadcrumbText: No Camera Enhancer
---

# Configuring the Barcode Reader SDK without the Camera Enhancer

In the `Getting Started` guide, we started with adding the camera control via the Camera Enhancer SDK, also called `DCE`. However, you might come across a scenario where you cannot use `DCE` and so have to use the [`CameraX`](https://developer.android.com/training/camerax) API. 

In this guide, we explore how to build an application using the Barcode Reader SDK, but this time without the use of the `DCE` API to control the camera. The creation of the application follows the same procedure as the regular guide, so let's skip to including the frameworks:

## Using CameraX with DBR

Before moving forward, please note that the full code of this sample is available in our repository ([DecodeWithCameraX](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/DecodeWithCameraX)). 

Normally the camera enhancer would be used to set up the video session, but instead we will use the `CameraX` API to create the video feed. The feed output is then used by DBR for the decoding process, via the [`decodeBuffer`](../api-reference/primary-decode.md#decodebuffer) method. Here is a quick snippet to showcase how the session would be set up.

**Code Snippet**

```java
cameraProviderFuture.addListener(() -> {
    try {
        // Camera provider is now guaranteed to be available
        ProcessCameraProvider cameraProvider = cameraProviderFuture.get();

        // Set up the view finder use case to display camera preview
        Preview preview = new Preview.Builder()
                .setTargetResolution(resolution)
                .build();

        // Choose the camera by requiring a lens facing
        CameraSelector cameraSelector = new CameraSelector.Builder()
                .requireLensFacing(LENS_FACING_BACK)
                .build();

        ImageAnalysis imageAnalysis =
                new ImageAnalysis.Builder()
                        // enable the following line if RGBA output is needed.
//                                .setOutputImageFormat(ImageAnalysis.OUTPUT_IMAGE_FORMAT_RGBA_8888)
                        .setTargetResolution(resolution)
                        .setBackpressureStrategy(ImageAnalysis.STRATEGY_KEEP_ONLY_LATEST)
                        .build();

        if (imageAnalysis.getOutputImageFormat() == ImageAnalysis.OUTPUT_IMAGE_FORMAT_RGBA_8888) {
            mImagePixelFormat = EnumImagePixelFormat.IPF_ABGR_8888;
        } else if (imageAnalysis.getOutputImageFormat() == ImageAnalysis.OUTPUT_IMAGE_FORMAT_YUV_420_888) {
            mImagePixelFormat = EnumImagePixelFormat.IPF_NV21;
        }

        imageAnalysis.setAnalyzer(Executors.newSingleThreadExecutor(), mBarcodeAnalyzer);

        // Attach use cases to the camera with the same lifecycle owner
        Camera camera = cameraProvider.bindToLifecycle(
                ((LifecycleOwner) this),
                cameraSelector,
                preview,
                imageAnalysis);

        // Connect the preview use case to the previewView
        preview.setSurfaceProvider(
                mPreviewView.getSurfaceProvider());
    } catch (InterruptedException | ExecutionException e) {
        // Currently no exceptions thrown. cameraProviderFuture.get()
        // shouldn't block since the listener is being called, so no need to
        // handle InterruptedException.
    }
}, ContextCompat.getMainExecutor(this));
```

The output is then analyzed and it is there where the `decodeBuffer` method is used to pick up any barcodes from the video stream. Please refer to the following for more info on the implementation of the analyzer.

```java
private ImageAnalysis.Analyzer mBarcodeAnalyzer = new ImageAnalysis.Analyzer() {
    @Override
    public void analyze(@NonNull ImageProxy imageProxy) {
        try {
            // insert your code here.
            // after done, release the ImageProxy object
            if(isShowingDialog) {
                return;
            }
            byte[] data = new byte[imageProxy.getPlanes()[0].getBuffer().remaining()];
            imageProxy.getPlanes()[0].getBuffer().get(data);
            int nRowStride = imageProxy.getPlanes()[0].getRowStride();
            int nPixelStride = imageProxy.getPlanes()[0].getPixelStride();
            try {
                TextResult[] results = mReader.decodeBuffer(data,
                        nRowStride/nPixelStride, imageProxy.getHeight(), nRowStride,
                        mImagePixelFormat);
                runOnUiThread(() -> {
                    if(!isShowingDialog && results != null && results.length > 0) {
                        showResult(results);
                    }
                });
            } catch (BarcodeReaderException e) {
                e.printStackTrace();
            }
        } finally {
            imageProxy.close();
        }
    }
};
```

Once these are properly implemented along with the other components of the application (please see the full code for reference), the app is ready to be built and run on your Android device.

**Related API**
- Method [`decodeBuffer`](../api-reference/primary-decode.md#decodebuffer)
- API [`CameraX`](https://developer.android.com/training/camerax)