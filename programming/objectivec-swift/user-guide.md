---
layout: default-layout
title: Dynamsoft Barcode Reader for Objective-C & Swift - User Guide v8.4.1
description: This is the user guide v8.4.1 of Dynamsoft Barcode Reader for iOS SDK.
keywords: user guide, objective-c, oc, swift
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---


# User Guide for Objective-C & Swift

- System Requirements:
  - macOS 10.11 and above.
  - iOS 9.0 and above.
- Environment: Xcode 7.1 - 11.5 and above.
- Recommended: macOS 10.15.4+, Xcode 11.5+, iOS 11+

## Installation

To install Dynamsoft Barcode Reader for iOS on your development machine, you can download the SDK from the [Dynamsoft website](https://www.dynamsoft.com/Downloads/Dynamic-Barcode-Reader-Download.aspx) and unzip `dbr-ios-{version-number}.zip`.

After decompression, you can find samples in the **DBRSamples** folder under the **dbr-ios-{version-number}** folder.

## Getting Started: HelloWorld

In this section, you will be guide on creating a Hello world app which can read barcodes from camera video input. `Dynamsoft Camera Enhancer` will be used to deploy the camera video input module in this guide. Please follow the steps below.

1. Create a new iOS project in Xcode.
2. Add the barcode reader framework to your project

   - Unzip the downloaded ZIP file `dbr-ios-{version number}.zip` and you'll see `DynamsoftBarcodeReader.framework` and `DynamsoftCameraEnhancer.framework`.

   - Drag and drop the framework into your Xcode project. Make sure to check Copy items if needed and Create groups to copy the framework into your project's folder.

3. Add the required `.tbd/.dylib` file to your project.
   Go to the `Build Phases` tab of your Xcode project, under `Link Binary with Libraries` section, click + button. Search for the file `libc++.tbd`, select it and click Add button. Then the libc++.tbd file will be copied to your project.

4. Import the framework's header.

   Objective-C:

   ```objc
   #import <DynamsoftBarcodeReader/DynamsoftBarcodeSDK.h>
   #import <DynamsoftCameraEnhancer/DynamsoftCameraEnhancer.h>
   ```

   Swift:

   ```Swift
   import DynamsoftBarcodeReader
   import DynamsoftCameraEnhancer
   ```

5. Add code for barcode scanning

   After setting up the basic project, you can now move on to coding.

   The following code demonstrates initializing DynamsoftBarcodeReader and starting the barcode recognition process.

   Objective-C:

    ```objc
    #import "ViewController.h"
    #import <DynamsoftBarcodeReader/DynamsoftBarcodeReader.h>
    #import <DynamsoftCameraEnhancer/DynamsoftCameraEnhancer.h>
    @interface ViewController ()
    @property(nonatomic, strong) DynamsoftBarcodeReader *barcodeReader;
    @property(nonatomic, strong) DynamsoftCameraEnhancer *dce;
    @property(nonatomic, strong) DCECaptureView *dceView;
   
    @end
    
    @implementation ViewController
   
    - (void)viewDidLoad {
        [super viewDidLoad];
        [self initDBR];
        [self configurationDCE];
    }

    - (void)viewWillAppear:(BOOL)animated {
        [super viewWillAppear:animated];
    }

    /*Initialize Dynamsoft Barcode Reader from License Tracking Server.*/
    - (void)initDBR{
        iDMLTSConnectionParameters* dbrPara = [[iDMLTSConnectionParameters alloc] init];
        //Initialize DBR License
        dbrPara.organizationID = @"Put your organizationID here";
        _barcodeReader = [[DynamsoftBarcodeReader alloc] initLicenseFromLTS:dbrPara verificationDelegate:self];
        [_barcodeReader setModeArgument:@"BinarizationModes" index:0 argumentName:@"EnableFillBinaryVacancy" argumentValue:@"0" error:nil];
        [_barcodeReader setModeArgument:@"BinarizationModes" index:0 argumentName:@"BlockSizeX" argumentValue:@"81" error:nil];
        [_barcodeReader setModeArgument:@"BinarizationModes" index:0 argumentName:@"BlockSizeY" argumentValue:@"81" error:nil];
    }

    /*Deploy the camera with Dynamsoft Camera Enhancer.*/
    - (void)configurationDCE{
        _dceView = [DCECaptureView captureWithFrame:self.view.bounds];
        [_dceView addOverlay];
        [self.view addSubview:_dceView];
        iDCELTSConnectionParameters* dcePara = [[iDCELTSConnectionParameters alloc] init];
        dcePara.organizationID = @"Put your organizationID here";
        _dce = [[DynamsoftCameraEnhancer alloc] initLicenseFromLTS:dcePara;        
        view:_dceView verificationDelegate:self];
        [_dce setCameraDesiredState:CAMERA_STATE_ON];
        _dce.isEnable = YES;
        DCESettingParameters* para = [[DCESettingParameter alloc] init];
        para.cameraInstance = _dce;
        para.textResultDelegate = self;
        [_barcodeReader setCameraEnhancerPara:para];
    }

    - (void)CameraLTSLicenseVerificationCallback:(bool)isSuccess error:(NSError *)error{
        NSLog(@"Verification: %@",error.userInfo);
    }

    /*Get and display the text result.*/
    - (void)textResultCallback:(NSInteger)frameId results:(NSArray<iTextResult *> *)results userData:(NSObject *)userData{
        if (results.count > 0) {
            _dce.isEnable = NO;
            __weak ViewController *weakSelf = self;
            [self showResult:results.firstObject.barcodeText
                completion:^{
                    weakSelf.dce.isEnable = YES;
                }];
        }else{
            return;
        }
    }

    /*This is the function for displaying decode result on the screen*/
    - (void)showResult:(NSString *)result completion:(void (^)(void))completion {
        dispatch_async(dispatch_get_main_queue(), ^{
            UIAlertController *alert = [UIAlertController alertControllerWithTitle:result message:nil preferredStyle:UIAlertControllerStyleAlert];
            [alert addAction:[UIAlertAction actionWithTitle:@"OK" style:UIAlertActionStyleDefault
                                                    handler:^(UIAlertAction * action) {
                                                        completion();
                                                    }]];
            [self presentViewController:alert animated:YES completion:nil];
        });
    }

    @end
    ```

    Swift:

    ```Swift
    import UIKit
    import DynamsoftBarcodeReader
    import DynamsoftCameraEnhancer

    class ViewController: UIViewController, CameraLTSLicenseVerificationDelegate, DBRTextResultDelegate {
        
        var dce:DynamsoftCameraEnhancer! = nil
        var dceView:DCECaptureView! = nil
        var barcodeReader:DynamsoftBarcodeReader! = nil
        override func viewDidLoad() {
            super.viewDidLoad()
            initDBR()
            configurationDCE()
        }

        override func viewWillAppear(_ animated: Bool) {
            super.viewWillAppear(animated)
        }
        
        func initDBR() {
            /*Initialize Dynamsoft Barcode Reader from License Tracking Server.*/
            let lts = iDMLTSConnectionParameters()
            lts.organizationID = "Put your organizationID here"
            barcodeReader = DynamsoftBarcodeReader(licenseFromLTS: lts, verificationDelegate: self)
            barcodeReader.setModeArgument("BinarizationModes", index: 0, argumentName: "EnableFillBinaryVacancy", argumentValue: "0", error: nil)
            barcodeReader.setModeArgument("BinarizationModes", index: 0, argumentName: "BlockSizeX", argumentValue: "81", error: nil)
            barcodeReader.setModeArgument("BinarizationModes", index: 0, argumentName: "BlockSizeY", argumentValue: "81", error: nil)
        }
        /*Deploy the camera with Dynamsoft Camera Enhancer.*/
        func configurationDCE() {
            dceView = DCECaptureView.init(view: self.view.bounds)
            dceView.addOverlay()
            self.view.addSubview(dceView)
            let lts = iDCELTSConnectionParameters()
            lts.organizationID = "Put your organizationID here"
            dce = DynamsoftCameraEnhancer.init(licenseFromLTS: lts, view: dceView, verificationDelegate: self)
            dce.setCameraDesiredState(.CAMERA_STATE_ON)
            /*Set DCE setting parameters in Dynamsoft Barcode Reader.
            The camera instance will be transferred as an argument to the barcode reader.
            With the Camera instance, the barcode reader will automatically use decodeBuffer as the decode method.*/
            let para = DCESettingParameters.init()
            para.cameraInstance = dce
            para.textResultDelegate = self
            barcodeReader.setCameraEnhancerPara(para)
        }

        func cameraLTSLicenseVerificationCallback(_ isSuccess: Bool, error: Error?) {
            print("Verification: \(String(describing: error))")
        }
        /*Get and display the text result.*/
        func textResultCallback(_ frameId: Int, results: [iTextResult]?, userData: NSObject?) {
            if results!.count > 0 {
                dce.isEnable = false
                showResult(results!.first!.barcodeText!) { [weak self] in
                    self?.dce.isEnable = true
                }
            }else{
                return
            }
        }
        /*This is the function for displaying decode result on the screen*/
        private func showResult(_ result: String, completion: @escaping () -> Void) {
            DispatchQueue.main.async {
                let alert = UIAlertController(title: result, message: nil, preferredStyle: .alert)
                alert.addAction(UIAlertAction(title: "OK", style: .default, handler: { _ in completion() }))
                self.present(alert, animated: true, completion: nil)
            }
        }
    }
    ```

## Decoding Methods

The SDK provides multiple decoding methods that support reading barcodes from different sources, including static images,
video stream, files in memory, base64 string, bitmap, etc. Here is a list of all decoding methods:

- [decodeFile](api-reference/methods/decode.md#decodefilewithname): Reads barcodes from a specified file (BMP, JPEG, PNG, GIF, TIFF or PDF).
- [decodebase64](api-reference/methods/decode.md#decodebase64): Reads barcodes from a base64 encoded string of a file.  
- [decodeBuffer](api-reference/methods/decode.md#decodebuffer): Reads barcodes from raw buffer.
- [decodeImage](api-reference/methods/decode.md#decodeimage): Decodes barcodes from an image file in memory.

You can find more samples in more programming languages at [Code Gallery](https://www.dynamsoft.com/Downloads/Dynamic-Barcode-Reader-Sample-Download.aspx).

## Barcode Reading Settings

Calling the [decoding methods](#decoding-methods) directly will use the default scanning modes and it will satisfy most of the needs. The SDK also allows you to adjust the scanning settings to optimize the scanning performance for different usage scenarios.

### Use [`PublicRuntimeSettings`](api-reference/class/iPublicRuntimeSettings.md) class to Change Settings

Here are some typical scanning settings you might find helpful:

- [Specify Barcode Type to Read](#specify-barcode-type-to-read)
- [Specify Maximum Barcode Count](#specify-maximum-barcode-count)
- [Specify a Scan Region](#specify-a-scan-region)

For more scanning settings guide, please read the [How To Guide]({{site.how-to}}) section.

#### Specify Barcode Type to Read

A simple barcode format setting will result in a higher processing speed. By default, the SDK will read all the supported barcode formats except Postal Codes and Dotcode from the image. Please use the [`BarcodeFormatIds`]({{ site.enumerations }}format-enums.html#barcodeformat) and [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2) to specify your barcode format(s) so that you can find the balance between speed and readability.

#### Specify maximum barcode count

By default, the SDK will try to find at least one barcode. You can use `expectedBarcodesCount` to specify the maximum number of barcodes. If you set the maximum number of barcodes n, the SDK will try to find at least n barcodes. The scanning process will not stop until n barcodes are found or timeout.

#### Specify a scan region

By default, the barcode reader will scan the whole image for barcodes. This can lead to poor performance, especially when dealing with high-resolution images. You can speed up the recognition process by restricting the scanning region.

#### Code Snippet of PublicRuntimeSettings

The following code is a template on how to use `PublicRuntimeSettings`.

Objective-C:

```objc
iPublicRuntimeSettings* settings = [barcodeReader getRuntimeSettings:nil];
// Set the barcode format
settings.barcodeFormatIds = EnumBarcodeFormatONED;
settings.expectedBarcodesCount = 1;
// Set the scan region
//The following code shrinks the decoding region by 25% on all sides
settings.region.regionTop = 25;
settings.region.regionBottom = 75;
settings.region.regionLeft = 25;
settings.region.regionRight = 75;
//The region is determined by percentage
settings.region.regionMeasuredByPercentage = 1;
[barcodeReader updateRuntimeSettings:settings error:&error];
```

Swift:

```Swift
let settings = try reader.getRuntimeSettings()
// Set the barcode format
settings.barcodeFormatIds = Int(EnumBarcodeFormat.ONED.rawValue)
settings.expectedBarcodesCount = 1
// Set the scan region
//The following code shrinks the decoding region by 25% on all sides
settings.region.regionTop = 25
settings.region.regionBottom = 75
settings.region.regionLeft = 25
settings.region.regionRight = 75
//The region is determined by percentage
settings.region.regionMeasuredByPercentage = 1
reader.update(settings, error: nil)
```
