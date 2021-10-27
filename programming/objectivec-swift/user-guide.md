---
layout: default-layout
title: Dynamsoft Barcode Reader for Objective-C & Swift - User Guide v8.4.1
description: This is the user guide v8.4.1 of Dynamsoft Barcode Reader for iOS SDK.
keywords: user guide, objective-c, oc, swift
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---


# User Guide for Objective-C & Swift

## Requirements

- Operating systems:
  - macOS 10.11 and above.
  - iOS 9.0 and above.
- Environment: Xcode 7.1 - 11.5 and above.
- Recommended: macOS 10.15.4+, Xcode 11.5+, iOS 11+

## Installation

If you have downloaded the SDK from the <a href="https://www.dynamsoft.com/barcode-reader/downloads/?utm_source=docs" target="_blank">Dynamsoft website</a> and unzipped **dbr-ios-{version-number}.zip**, you can find two **frameworks** in the root folder. You can simply include `DynamsoftBarcodeReader.framework` to your project to start creating a barcode scanning app. The other framework, `DynamsoftCameraEnhancer.framework`, is an extension package that integrates video frame preprocessing algorithms and camera control APIs.

| Framework | Description |
| --------- | ----------- |
| `DynamsoftBarcodeReader.framework` | The Barcode Reader package, including all barcode decoding related algorithms and APIs. |
| `DynamsoftCameraEnhancer.framework` | The Camera Enhancer package, including camera control APIs and frame preprocessing algorithm.  |

## Build Your First Application

In this section, let’s see how to create a **HelloWorld** app for reading barcodes from camera video input.

> Note:
>- You can download the similar complete Objective-C source code from [here](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/HelloWorldObjc)
>- You can download the similar complete Swift source code from [here](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/HelloWorldSwift)

### Create a New Project

1. Open the Xcode and select create a new project.

2. Select **iOS > App** for your application.

3. Input your product name (DBRHelloworld), interface (StoryBoard) and language (Objective-C/Swift).

4. Click on the **Next** button and select the location to save the project.

5. Click on the **Create** button to finish.

### Include the Frameworks

You can add your downloaded frameworks into your project by the following steps:

1. Drag and drop the **DynamsoftBarcodeReader** and **DynamsoftCameraEnhancer** frameworks into your Xcode project. Make sure to check Copy items if needed and Create groups to copy the framework into your project's folder.

2. Click on the project. Go to the **General > Frameworks > Libraries and Embedded Content**. Set the **embed type** to **Embed & Sign**.

3. Add the required **.tbd/.dylib** file to your project. Go to the **Build Phases** tab of your Xcode project, under **Link Binary with Libraries** section, click + button. Search for the file **libc++.tbd**, select it and click Add button. Then the **libc++.tbd** file will be copied to your project.

4. Import the headers.

   Objective-C:

   ```objc
   #import <DynamsoftBarcodeReader/DynamsoftBarcodeReader.h>
   #import <DynamsoftCameraEnhancer/DynamsoftCameraEnhancer.h>
   ```

   Swift:

   ```Swift
   import DynamsoftBarcodeReader
   import DynamsoftCameraEnhancer
   ```

### Configure the Camera

1. Create an instance of **DynamsoftCameraEnhancer** for getting video input.

    Objective-C:

    ```objc
    /*Initialize DynamsoftCameraEnhancer and DCECameraView*/
    @property(nonatomic, strong) DynamsoftCameraEnhancer *dce;
    @property(nonatomic, strong) DCECameraView *dceView;

    /*
    ...
    */

    - (void)viewDidLoad {
        [super viewDidLoad];
        [self configurationDCE];
    }
    ```

    Swift:

    ```swift
    /*Initialize DynamsoftCameraEnhancer and DCECameraView*/ 
    var dce:DynamsoftCameraEnhancer! = nil
    var dceView:DCECameraView! = nil

    /*
    ...
    */

    override func viewDidLoad() {
        super.viewDidLoad()
        configurationDCE()
    }
    ```

2. Add configurations for **DynamsoftCameraEnhancer**.

    Objective-C:

    ```objectivec
    /*Configure the Camera Enhancer.*/
    - (void)configurationDCE{
        _dceView = [DCECameraView cameraWithFrame:self.view.bounds];
        [self.view.addSubView:_dceView];

        /*Display overlays on the decoded barcodes*/
        [_dceView setOverlayVisible:true];

        /*The string "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" here will grant you a public trial license good for 7 days. After that, please visit: https://www.dynamsoft.com/customer/license/trialLicense?product=dce&utm_source=installer&package=ios to request for 30 days extension.*/
        [DynamsoftCameraEnhancer initLicense:@"DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" verificationDelegate:self];
        _dce = [[DynamsoftCameraEnhancer alloc] initWithView:_dceView];
        [_dce open];
        [_dce addListener:self];
        [_dce setFrameRate:30];
    }
    ```

    Swift:

    ```swift
    /*Configure the Camera Enhancer.*/
    func configurationDCE() {
        dceView = DCECameraView.init(frame: self.view.bounds)
        self.view.addSubview(dceView)

        /*Display overlays on the decoded barcodes*/
        dceView.setOverlayVisible(true)

        /*The string "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" here will grant you a public trial license good for 7 days. After that, please visit: https://www.dynamsoft.com/customer/license/trialLicense?product=dce&utm_source=installer&package=ios to request for 30 days extension.*/
        DynamsoftCameraEnhancer.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9", verificationDelegate: self)
        dce = DynamsoftCameraEnhancer.init(view: dceView)
        dce.open()
        dce.setFrameRate(30)
        dce.addListener(self)
    }
    ```

### Configure the Barcode Reader

1. Create an instance of the Barcode reader.

    Objective-C:

    ```objectivec
    @property(nonatomic, strong) DynamsoftBarcodeReader *barcodeReader;

    /*
    ...
    */

    - (void)viewDidLoad {
        [self configurationDBR];
    }
    ```

    Swift:

    Create instance of the Barcode reader:

    ```swift
    var barcodeReader:DynamsoftBarcodeReader! = nil

    /*
    ...
    */

    override func viewDidLoad() {
        configurationDBR()
    }
    ```

2. Add configurations to the barcode reader and initialize the license.

    Objective-C:

    ```objectivec
    - (void)configurationDBR{
        iDMDLSConnectionParameters* lts = [[iDMDLSConnectionParameters alloc] init];
        // 7 days free trial will be available for new users.
        // Please visit: https://www.dynamsoft.com/customer/license/trialLicense?product=dbr&utm_source=installer&package=ios to get extension and more information about license.
        lts.organizationID = @"200001";
        _barcodeReader = [[DynamsoftBarcodeReader alloc] initLicenseFromDLS:lts verificationDelegate:self];
        NSError *error = [[NSError alloc] init];
    }
    ```

    Swift:

    ```swift
    func configurationDBR() {
        let dls = iDMDLSConnectionParameters()
        // 7 days free trial will be available for new users.
        // Please visit: https://www.dynamsoft.com/customer/license/trialLicense?product=dbr&utm_source=installer&package=ios to get extension and more information about license.
        dls.organizationID = "200001"
        barcodeReader = DynamsoftBarcodeReader(licenseFromDLS: dls, verificationDelegate: self)
        var error : NSError? = NSError()
    }
    ```

3. Create `textResultcallback` to obtain the recognized barcode results.

    Objective-C:

    ```objc
    - (void)textResultCallback:(NSInteger)frameId results:(NSArray<iTextResult *> *)results userData:(NSObject *)userData{
        if (results.count > 0) {
            [_dce pause];
            __weak ViewController *weakSelf = self;
            NSString *title = @"Results";
            NSString *msgText = @"";
            NSString *msg = @"Please visit: https://www.dynamsoft.com/customer/license/trialLicense?";
            for (NSInteger i = 0; i< [results count]; i++) {
                if (results[i].exception != nil && [results[i].exception containsString:msg]) {
                    msgText = [msg stringByAppendingString:@"product=dbr&utm_source=installer&package=ios to request for 30 days extension."];
                    title = @"Exception";
                    break;
                }
                if (results[i].barcodeFormat_2 != 0) {
                    msgText = [msgText stringByAppendingString:[NSString stringWithFormat:@"\nFormat: %@\nText: %@\n", results[i].barcodeFormatString_2, results[i].barcodeText]];
                }else{
                    msgText = [msgText stringByAppendingString:[NSString stringWithFormat:@"\nFormat: %@\nText: %@\n", results[i].barcodeFormatString, results[i].barcodeText]];
                }
            }
            [self showResult:title
                        msg:msgText
                    acTitle:@"OK"
                completion:^{
                    [weakSelf.dce resume];
                }];
        }else{
            return;
        }
    }
    ```

    Swift:

    ```swift
    func textResultCallback(_ frameId: Int, results: [iTextResult]?, userData: NSObject?) {
        if results!.count > 0 {
            dce.pause()
            var msgText:String = ""
            var title:String = "Results"
            let msg = "Please visit: https://www.dynamsoft.com/customer/license/trialLicense?"
            for item in results! {
                if results!.first!.exception != nil && results!.first!.exception!.contains(msg) {
                    msgText = "\(msg)product=dbr&utm_source=installer&package=ios to request for 30 days extension."
                    title = "Exception"
                    break
                }
                if item.barcodeFormat_2.rawValue != 0 {
                    msgText = msgText + String(format:"\nFormat: %@\nText: %@\n", item.barcodeFormatString_2!, item.barcodeText ?? "noResuslt")
                }else{
                    msgText = msgText + String(format:"\nFormat: %@\nText: %@\n", item.barcodeFormatString!,item.barcodeText ?? "noResuslt")
                }
            }
            showResult(title, msgText, "OK") {[weak self] in
                self?.dce.resume()
            }
        }else{
            return
        }
    }
    ```

4. Create settings of video barcode reading and bind to Barcode Reader object.

    Objective-C:

    ```objectivec
    // Create settings of video barcode reading.
    DCESettingParameters* para = [[DCESettingParameter alloc] init];
    // This cameraInstance is the instance of the Dynamsoft Camera Enhancer.
    // The Barcode Reader will use this instance to take control of the camera and acquire frames from the camera to start the barcode decoding process.
    para.cameraInstance = _dce;
    // Make this setting to get the result. The result will be an object that contains text result and other barcode information.
    para.textResultDelegate = self;
    // Bind the Camera Enhancer instance to the Barcode Reader instance.
    [_barcodeReader setCameraEnhancerPara:para];
    ```

    Swift:

    ```swift
    // Create settings of video barcode reading.
    let para = DCESettingParameters.init()
    // This cameraInstance is the instance of the Dynamsoft Camera Enhancer.
    // The Barcode Reader will use this instance to take control of the camera and acquire frames from the camera to start the barcode decoding process.
    para.cameraInstance = dce
    // Make this setting to get the result. The result will be an object that contains text result and other barcode information.
    para.textResultDelegate = self
    // Bind the Camera Enhancer instance to the Barcode Reader instance.
    barcodeReader.setCameraEnhancerPara(para)
    ```

### Additional Steps

Add showText method to display the barcode results on the UI.

Objective-C:

```objectivec
- (void)showResult:(NSString *)title msg:(NSString *)msg acTitle:(NSString *)acTitle completion:(void (^)(void))completion {
    dispatch_async(dispatch_get_main_queue(), ^{
        UIAlertController *alert = [UIAlertController alertControllerWithTitle:title message:msg preferredStyle:UIAlertControllerStyleAlert];
        [alert addAction:[UIAlertAction actionWithTitle:acTitle style:UIAlertActionStyleDefault
                                                handler:^(UIAlertAction * action) {
                                                    completion();
                                                }]];
        [self presentViewController:alert animated:YES completion:nil];
    });
}
```

Swift:

```swift
private func showResult(_ title: String, _ msg: String, _ acTitle: String, completion: @escaping () -> Void) {
    DispatchQueue.main.async {
        let alert = UIAlertController(title: title, message: msg, preferredStyle: .alert)
        alert.addAction(UIAlertAction(title: acTitle, style: .default, handler: { _ in completion() }))
        self.present(alert, animated: true, completion: nil)
    }
}
```

### Run the Project

If you have followed the above guide step by step, your project will be able to build a video barcode scanner. If the project is not working well, please visit the github to get the similar complete source code:
>- [Objective-C source code](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Objective-C/HelloWorldObjC)
>- [Swift source code](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Swift/HelloWorldSwift)

## Further Barcode Reading Settings

Regular barcode reading settings and modes parameter settings are available via [`PublicRuntimeSettings`](api-reference/auxiliary-iPublicRuntimeSettings.md) and JSON templates. The following typical settings you might find helpful:

- [Specify Barcode Formats]({{ site.oc }}samples/general.html#specify-barcode-format-and-barcode-count)
- [Specify the Barcode Count]({{ site.oc }}samples/general.html#specify-barcode-format-and-barcode-count)
- [Specify the Scan Region]({{ site.oc }}samples/general.html#specify-the-scan-region)
- [Speed first barcode reading settings]({{ site.oc }}samples/speed.html)
- [Read-rate first barcode reading settings]({{ site.oc }}samples/read-rate.html)
- [Accuracy first barcode reading settings]({{ site.oc }}samples/accuracy.html)

For more scanning settings guide, please check the [How To Guide]({{site.introduction}}how-to-guide/){:target="_blank"} section.

## Known Issues

### "dyld: Library not loaded" error on app initialization

You might run into this error in the app initialization phase - and in order to resolve this, a slight change needs to be done to the build settings of the project. Please make sure that you take the following steps to avoid this error:

- When adding the Barcode Reader framework in step 2 of the above instructions, make sure to tick off the **Copy items if needed** and **Create groups** options.
- In the **Build Settings** of the project, find the **Validate Workspace** setting and make sure it is set to **Yes**.
- In **General > Frameworks > Libraries and Embedded Content**, make sure that the **DynamsoftBarcodeReader.framework** is set to **Embed & Sign**.

### "Unsupported Architectures" error when building and releasing the application for the App Store

The error seems to stem from the inclusion of the **x86_64** architecture in **DynamsoftBarcodeReader.framework**. This error can potentially happen with dynamic libraries (like DBR iOS) that have pieces for all architectures, including devices and simulators.

This specific error references the **x86_64** architecture which is for the iPhone simulator. When releasing to the App Store, the simulator architectures (**x86_64**) need to be removed from the dynamic library before the project is built for the App Store.

In order to solve the issue, add a **Run Script** phase after the **Embed Frameworks** step of the **Build Phases**, set it to use **/bin/sh**, and use the following script:

```ruby
APP_PATH="${TARGET_BUILD_DIR}/${WRAPPER_NAME}"

# This script loops through the frameworks embedded in the application and
# removes unused architectures.
find "$APP_PATH" -name '*.framework' -type d | while read -r FRAMEWORK
do
    FRAMEWORK_EXECUTABLE_NAME=$(defaults read "$FRAMEWORK/Info.plist" CFBundleExecutable)
    FRAMEWORK_EXECUTABLE_PATH="$FRAMEWORK/$FRAMEWORK_EXECUTABLE_NAME"
    echo "Executable is $FRAMEWORK_EXECUTABLE_PATH"

    EXTRACTED_ARCHS=()

    for ARCH in $ARCHS
    do
        echo "Extracting $ARCH from $FRAMEWORK_EXECUTABLE_NAME"
        lipo -extract "$ARCH" "$FRAMEWORK_EXECUTABLE_PATH" -o "$FRAMEWORK_EXECUTABLE_PATH-$ARCH"
        EXTRACTED_ARCHS+=("$FRAMEWORK_EXECUTABLE_PATH-$ARCH")
    done

    echo "Merging extracted architectures: ${ARCHS}"
    lipo -o "$FRAMEWORK_EXECUTABLE_PATH-merged" -create "${EXTRACTED_ARCHS[@]}"
    rm "${EXTRACTED_ARCHS[@]}"

    echo "Replacing original executable with thinned version"
    rm "$FRAMEWORK_EXECUTABLE_PATH"
    mv "$FRAMEWORK_EXECUTABLE_PATH-merged" "$FRAMEWORK_EXECUTABLE_PATH"

done
```

The script looks through your built application's **Frameworks** folder and make sure only the architectures you're building for are the only ones included in each framework. This way, you don't have to worry about dealing with those arcitectures during the build process.
