---
layout: default-layout
title: Dynamsoft Barcode Reader for iOS - How to use the Barcode Reader without the Camera Enhancer
description: This is the Advanced Usage page of Dynamsoft Barcode Reader for iOS SDK.
keywords: iOS, sample, Android, camera
needAutoGenerateSidebar: true
breadcrumbText: DBRwithoutDCE
---

# Configuring the Barcode Reader SDK without the Camera Enhancer

In the `Getting Started` guide, we started with adding the camera control via the Camera Enhancer SDK, also called `DCE`. However, you might come across a scenario where you cannot use `DCE` and so have to use the `AVCapture` API. In this guide, we explore how to build an application using the Barcode Reader SDK, but this time without the use of the `DCE` API to control the camera. The creation of the application follows the same procedure as the regular guide, so let's skip to including the frameworks:

## Building the Application

Before moving forward, please note that the full code of this sample is available upon request by contacting the [Dynamsoft Support Team](https://www.dynamsoft.com/company/contact/#:~:text=To%20schedule%20an%20online%20meeting,at%20support%40dynamsoft.com.). This time, since we are not including the Camera Enhancer SDK, we just need to add the DynamsoftBarcodeReader framework:

1. Drag and drop and the **DynamsoftBarcodeReader** framework or xcframework into the Xcode project. Make sure to check Copy items if needed and Create groups to copy the framework into your project’s folder.

2. Click on the project then go to **General –> Frameworks, Libraries, and Embedded Content**. Set the **Embed** field to **Embed & Sign** for `DynamsoftBarcodeReader`.

3. Please click on the project again and go to **Build Phases -> Link Binary with Libraries** and add the `libc++.1.tbd` library.

4. Before we dive into the implementation of the `ViewController`, first we will create a `DbrManager` component that will control the barcode scanning component, including the barcode reader settings themselves as well as the video settings. Normally, this wouldn't be needed if DCE is being used as DCE provides the API to control the video and its various settings. So let's proceed with creating a new file in the project called `DbrManager`. For reference, the full `DbrManager` can be found **here**. You will notice that `DbrManager` implements many functions, so we will go through the most important ones.
    * `init(DLS | licenseKey)`: This method is responsible for initializing the barcode reader instance based on the input parameter, whether it is a DLS-based license or a regular trial license key, but not both at the same time.
    * `connectServerAfterInit`: A method that is called when the initialization fails using a DLS-based license and the user would like to try the initialization again.
    * `parametersInit`: Initializes the various parameters of the Barcode Reader as well as the video control
    * `setBarcodeFormat`: Specifies which barcode format(s) the SDK should pick up while in use
    * `setVideoSession`: Sets the video session that will be used to scan the barcodes.
    * `getAvailableCamera`: A method used in setVideoSession to list all the available cameras to the device.
    * `startVideoSession`: Starts the video session to begin the scanning process.
    * `captureOutput`: This is where the decoding of the frames happens using the `decodeBuffer` method of the DBR API.
    * `setRecognitionCallback`: Sets the recognition callback for the decode method.
    * `setServerLicenseVerificationCallback`: Sets the callback used during server verification when a DLS-based license is used for initialization.
    * `ltsLicenseVerificationCallback`: The callback for the DLS license verification process. This callback must be implmented when using a DLS-based license or else errors will occur during the build and initialization.
5. Once the `DbrManager` is created, then we can go back to the `ViewController` and start implementing that. Similar to DbrManager, the inner workings of this implementation could look a bit complicated so this guide will just quickly go over the most important methods and how they relate to DbrManager. For reference, you can find the full ViewController code **here**.
    * `viewDidLoad`: The main function that is triggered once the view is loaded. The DBR initialization happens here.
    * `configInterface`: Configures the main UI interface.
    * `onReadImageBufferComplete`: Used as the callback for the recognition process. So basically, it will deal with the barcode results once they are obtained from the frames.
    * `onVerificationCallBack`: Used as the callback for the initialization process of DBR should a DLS-based license get used.
    * `captureOutput`: The core method used to feed the video stream to the decode method of DBR to get any barcode results.

6. It is important to also make sure that the Storyboard of the application matches with the code. Therefore, we will need to place a UI item for each of the components defined in the ViewController code.
    * *rectLayerImage*: UIImageView component in the centre of the screen.
    * *flashButton*: Button that is tied to the flash feature.
    * *detectDesclabel*: Label that informs the user to align the barcode according to the scanning area.
    * *choosePictureButton*: Button that is used to open the photo gallery and choose a photo to decode instead of using the camera.
7. Once all the code is in place and everything is checked, then we can build the app. If everything is correct, and is implemented similar to the sample code, then the build should be successful.

8. The app can then be run on your iPhone (given that it's a supported model).

