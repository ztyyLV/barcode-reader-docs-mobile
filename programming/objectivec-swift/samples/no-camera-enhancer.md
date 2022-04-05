---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - How to use the Barcode Reader without the Camera Enhancer
description: This is the Advanced Usage page of Dynamsoft Barcode Reader for iOS SDK.
keywords: iOS, sample, Android, camera
needAutoGenerateSidebar: true
breadcrumbText: No Camera Enhancer
---

# Configuring the Barcode Reader SDK without the Camera Enhancer

In the `Getting Started` guide, we started with adding the camera control via the Camera Enhancer SDK, also called `DCE`. However, you might come across a scenario where you cannot use `DCE` and so have to use the [`AVCaptureSession`](https://developer.apple.com/documentation/avfoundation/avcapturesession) API. 

In this guide, we explore how to build an application using the Barcode Reader SDK, but this time without the use of the `DCE` API to control the camera. The creation of the application follows the same procedure as the regular guide, so after including the barcode reader framework and doing the first step of the DBR initialization, we can address the video input.

## Using AVCaptureSession with DBR

Before moving forward, please note that the full code of this sample is available in our repository ([Swift](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Swift/DecodeWithAVCaptureSession)/[ObjectiveC](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Objective-C/DecodeWithAVCaptureSession)). 

Normally the camera enhancer would be used to set up the video session, but instead we will use the `AVCaptureSession` API to create the video feed. The feed output is then used by DBR for the decoding process, via the [`decodeBuffer`](../api-reference/primary-decode.md#decodebuffer) method. Here is a quick snippet to showcase how the session would be set up.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
- (void)setupSession
{
    self.captureSession = [[AVCaptureSession alloc]init];
    
    self.captureSession.sessionPreset = AVCaptureSessionPresetHigh;
    
    // Vedio
    AVCaptureDevice *vedioDevice = [AVCaptureDevice defaultDeviceWithMediaType:AVMediaTypeVideo];
    AVCaptureDeviceInput *deviceInput = [AVCaptureDeviceInput deviceInputWithDevice:vedioDevice error:nil];
    if (deviceInput){
        if([self.captureSession canAddInput:deviceInput]) {
            [self.captureSession addInput:deviceInput];
        }
    }
    self.movieOutput = [[AVCaptureMovieFileOutput alloc]init];
    if([self.captureSession canAddOutput:self.movieOutput]) {
        [self.captureSession addOutput:self.movieOutput];
    }
    
    if (@available(iOS 10.0, *)) {
        self.imageOutput = [[AVCapturePhotoOutput alloc]init];

        if ([self.captureSession canAddOutput:self.imageOutput]){
            [self.captureSession addOutput:self.imageOutput];
        }
    }else {
        self.stillImageOutput = [[AVCaptureStillImageOutput alloc]init];

        self.stillImageOutput.outputSettings = @{AVVideoCodecKey:AVVideoCodecTypeJPEG};
        if ([self.captureSession canAddOutput:self.stillImageOutput]){
            [self.captureSession addOutput:self.stillImageOutput];
        }
    }
    
    self.videoQueue = dispatch_queue_create("cc.VideoQueue", NULL);

    dispatch_async(self.videoQueue, ^{
        [self.captureSession startRunning];
    });
    
}
```
2. 
```swift
func setSession() {
    let session = AVCaptureSession.init()
    session.sessionPreset = .hd1920x1080
    let device = AVCaptureDevice.default(
        for: .video)
    var input: AVCaptureDeviceInput? = nil
    do {
        if let device = device {
            input = try AVCaptureDeviceInput(
                device: device)
        }
    } catch {
    }
    
    if (input == nil) {
        // Handling the error appropriately.
    }
    session.addInput(input!)
    
    let output = AVCaptureVideoDataOutput.init()
    session.addOutput(output)
    var queue:DispatchQueue
    queue = DispatchQueue(label: "queue")
    output.setSampleBufferDelegate(self as AVCaptureVideoDataOutputSampleBufferDelegate, queue: queue)
    output.videoSettings = [kCVPixelBufferPixelFormatTypeKey : kCVPixelFormatType_32BGRA] as [String : Any]
    
    let w = UIScreen.main.bounds.size.width
    let h = UIScreen.main.bounds.size.height
    var mainScreen = CGRect.zero
    mainScreen.size.width = min(w, h)
    mainScreen.size.height = max(w, h)
        
    let preLayer = AVCaptureVideoPreviewLayer(session: session)
    preLayer.frame = mainScreen
    preLayer.videoGravity = .resizeAspectFill
    view.layer.addSublayer(preLayer)
    session.startRunning()
}
```

Once these are set up, the corresponding capture output methods are implemented that will take the output and feed it to the barcode reader instance to find any barcodes.

For the full implementation of the `captureOutput`, it is best to refer to the full sample code linked above as there are a number of differences between the Objective-C and Swift implemenatations, with Swift being the more concise of the two.

**Related API**
- Method [`decodeBuffer`](../api-reference/primary-decode.md#decodebuffer)
- API [`AVCaptureSession`](https://developer.apple.com/documentation/avfoundation/avcapturesession)