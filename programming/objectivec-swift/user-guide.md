---
layout: default-layout
title: Dynamsoft Barcode Reader for Objective-C & Swift - User Guide v8.4.1
description: This is the user guide v8.4.1 of Dynamsoft Barcode Reader for iOS SDK.
keywords: user guide, objective-c, oc, swift
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---


# Getting Started with iOS

## Requirements

- Operating systems:
  - macOS 10.11 and above.
  - iOS 9.0 and above.
- Environment: Xcode 7.1 - 11.5 and above.
- Recommended: macOS 10.15.4+, Xcode 11.5+, iOS 11+

## Installation

If you have downloaded the SDK from the <a href="https://www.dynamsoft.com/barcode-reader/downloads/?utm_source=docs" target="_blank">Dynamsoft website</a> and unzipped **dbr-ios-{version-number}.zip**, you can find two **frameworks** in the root folder. You can simply include `DynamsoftBarcodeReader.framework` to your project to start creating a barcode scanning app. The other framework, `DynamsoftCameraEnhancer.framework`, is an extension package that integrates video frame preprocessing algorithms and camera control APIs.

Starting from v8.8 of DBR, the SDK also offers **xcframeworks** for iOS development. **xcframeworks** are slowly replacing **frameworks** as the standard for iOS development, so we are happy to now offer `DynamsoftBarcodeReader.xcframework` and `DynamsoftCameraEnhancer.xcframework` included as part of the SDK. To learn more about **xcframeworks** and what they offer over the regular **framework**, please check out this [article](https://medium.com/trueengineering/xcode-and-xcframeworks-new-format-of-packing-frameworks-ca15db2381d3) by TrueEngineering.

| Framework | Description |
|---------|-------------|
| `DynamsoftBarcodeReader.framework` <br /> `DynamsoftBarcodeReader.xcframework`| The Barcode Reader package, including all barcode decoding related algorithms and APIs. |
| `DynamsoftCameraEnhancer.framework` <br /> `DynamsoftCameraEnhancer.xcframework`| The Camera Enhancer package, including camera control APIs and frame preprocessing algorithm. |

## Build Your First Application

In this section, let's see how to create a **HelloWorld** app for reading barcodes from camera video input.

> Note:
>- You can download the complete Objective-C source code [here](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Objective-C/HelloWorldObjC)
>- You can download the complete Swift source code [here](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Swift/HelloWorldSwift)

### Create a New Project

1. Open Xcode and select create a new project.

2. Select **iOS > App** for your application.

3. Input your product name (DBRHelloworld), interface (StoryBoard) and language (Objective-C/Swift). We currently do not support SwiftUI, so we apologize if this causes any inconvenience.

4. Click on the **Next** button and select the location to save the project.

5. Click on the **Create** button to finish.

### Include the Frameworks

You can add your downloaded frameworks into your project through the following steps:

1. Drag and drop the **DynamsoftBarcodeReader** and **DynamsoftCameraEnhancer** frameworks into your Xcode project. Make sure to check Copy items if needed and Create groups to copy the framework into your project's folder.

2. Click on the project then go to  **General --> Frameworks, Libraries, and Embedded Content**. Set the **Embed** field to **Embed & Sign** for `DynamsoftBarcodeReader` and `DynamsoftCameraEnhancer`.

3. Import the headers in the `ViewController` file.

   Objective-C:

   ```objc
   #import <DynamsoftBarcodeReader/DynamsoftBarcodeReader.h>
   #import <DynamsoftCameraEnhancer/DynamsoftCameraEnhancer.h>
   ```

   Swift:

   ```swift
   import DynamsoftBarcodeReader
   import DynamsoftCameraEnhancer
   ```

### Let's Configure the Camera First

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

2. Add configurations for DynamsoftCameraEnhancer.

    Objective-C:

    ```objc
    /*Configure the Camera Enhancer.*/
    - (void)configurationDCE{
        _dceView = [DCECameraView cameraWithFrame:self.view.bounds];
        [self.view.addSubView:_dceView];

        /*Display overlays on the decoded barcodes*/
        [_dceView setOverlayVisible:true];
        _dce = [[DynamsoftCameraEnhancer alloc] initWithView:_dceView];
        [_dce open];
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
        dce = DynamsoftCameraEnhancer.init(view: dceView)
        dce.open()
    }
    ```

### Now to Add the Barcode Reader

1. Dynamsoft barcode reader needs a valid license to work. It is recommended to put the license activation code under the **AppDelegate** file.

    Add DBRLicenseVerificationListener to the **AppDelegate**:

    ```objc
    @interface AppDelegate ()<DBRLicenseVerificationListener>
    ```

    Swift:

    ```swift
    class AppDelegate: DBRLicenseVerificationListener{}
    ```

    Add the following code to initialize the license in method `application:didFinishLaunchingWithOptions:`:

    Objective-C:

    ```objc
    @implementation AppDelegate
    - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
        /*Initialize license for Dynamsoft Barcode Reader.*/
        /* The string "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" here is a time-limited public trial license. Note that network connection is required for this license to work.*/
        /* You can also request an extension for your trial license in the customer portal: https://www.dynamsoft.com/customer/license/trialLicense?product=dce&utm_source=installer&package=ios*/
        [DynamsoftBarcodeReader initLicense:@"DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" verificationDelegate:self];
        return YES;
    }

    -(void)DBRLicenseVerificationListener:(bool)isSuccess error:(NSError *)error{

    }
    ```

    Swift:

    ```swift
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        /*Initialize license for Dynamsoft Barcode Reader.*/
        /* The string "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" here is a time-limited public trial license. Note that network connection is required for this license to work.*/
        /* You can also request an extension for your trial license in the customer portal: https://www.dynamsoft.com/customer/license/trialLicense?product=dce&utm_source=installer&package=ios*/
        DynamsoftBarcodeReader.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9", verificationDelegate: self)
        return true
    }

    func dbrLicenseVerificationCallback(_ isSuccess: Bool, error: Error?) {

    }
    ```

2. Since we have initialized the license, we can move on to create an instance of the Barcode Reader. Go back to the `ViewController` file, declare and create the instance of barcodeReader:

    Objective-C:

    ```objc
    @property(nonatomic, strong) DynamsoftBarcodeReader *barcodeReader;

    - (void)viewDidLoad {
        [super viewDidLoad];
        [self configurationDBR];
    }

    - (void)configurationDBR {
        /* Create the instance */
        _barcodeReader = [[DynamsoftBarcodeReader alloc] init];
        /* You can add your barcode reader configurations here. */
    }
    ```

    Swift:

    ```swift
    var barcodeReader:DynamsoftBarcodeReader! = nil

    override func viewDidLoad() {
        super.viewDidLoad()
        configurationDBR()
    }

    func configurationDBR(){
        /* Create the instance */
        barcodeReader = DynamsoftBarcodeReader.init()
        /* You can add your barcode reader configurations here. */
    }
    ```

3. After both of the barcode reader instance and the camera enhancer instance are created, let's bind the camera enhancer instance to the barcode reader so that the barcode reader can get video streaming for barcode decoding. Add the following to the `configurationDCE` method:

    Objective-C:

    ```objc
    - (void)configurationDCE{
        // Bind the Camera Enhancer instance to the Barcode Reader instance.
        // The _dce is the instance of the Dynamsoft Camera Enhancer.
        // The Barcode Reader will use this instance to take control of the camera and acquire frames from the camera to start the barcode decoding process.
        [_barcodeReader setCameraEnhancer:_dce];
        // Start Scanning controls the process of video barcode decoding
        [_barcodeReader startScanning];
    }
    ```

    Swift:

    ```swift
    /*Deploy the camera with Dynamsoft Camera Enhancer.*/
    func configurationDCE() {
        /*Bind the Camera Enhancer instance to the Barcode Reader instance.
        The _dce is the instance of the Dynamsoft Camera Enhancer.
        The Barcode Reader will use this instance to take control of the camera and acquire frames from the camera to start the barcode decoding process.*/
        barcodeReader.setCameraEnhancer(dce)
        /* Start Scanning controls the process of video barcode decoding. */
        barcodeReader.startScanning()
    }
    ```

4. Once you have start the video barcode decoding thread, `TextResultCallback` is then implemented when barcode result is detected.

    To acquire the barcode `TextResult` with `TextResultCallback`, please firstly add the `DBRTextResultListener` to the `ViewController`.

    Objective-C:

    ```objc
    @interface ViewController ()<DBRTextResultListener>
    ```

    Swift:

    ```swift
    class ViewController: DBRTextResultListener{}
    ```

    Then implement the listener in the `ViewController`.

    Objective-C:

    ```objc
    - (void)textResultCallback:(NSInteger)frameId imageData:(iImageData *)imageData results:(NSArray<iTextResult *> *)results{
        if (results.count > 0) {
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
            
                }];
        }else{
            return;
        }
    }   
    ```

    Swift:

    ```swift
    func textResultCallback(_ frameId: Int, ImageData: iImageData, results: [iTextResult]?) {
        if results!.count > 0 {
            var msgText:String = ""
            var title:String = "Results"
            for item in results! {
                if item.barcodeFormat_2.rawValue != 0 {
                    msgText = msgText + String(format:"\nFormat: %@\nText: %@\n", item.barcodeFormatString_2!, item.barcodeText ?? "noResuslt")
                }else{
                    msgText = msgText + String(format:"\nFormat: %@\nText: %@\n", item.barcodeFormatString!,item.barcodeText ?? "noResuslt")
                }
            }
            showResult(title, msgText, "OK") {
            }
        }else{
            return
        }
    }
    ```

5. Bind the TextResultListener to the barcode reader.

    Objective-C:

    ```objc
    - (void)configurationDCE{
        [_barcodeReader setCameraEnhancer:_dce];
        // Make this setting to get the result. The result will be an object that contains text results and other barcode information.
        [_barcodeReader setDBRTextResultListener:self];
        [_barcodeReader startScanning];
    }
    ```

    Swift:

    ```swift
    func configurationDCE() {
        barcodeReader.setCameraEnhancer(dce)
        /* Make this setting to get the result. The result will be an object that contains text result and other barcode information. */
        barcodeReader.setDBRTextResultListener(self)
        barcodeReader.startScanning()
    }
    ```

6. Lastly, add the `showText` method to display the barcode results on the UI

    Objective-C:

    ```objc
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

1. Select the device that you want to run your app on.
2. Run the project, then your app will be installed on your device.

You can download the complete source code here:

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Objective-C/HelloWorldObjC" target="_blank">Objective-C source code</a>
- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/ios/Swift/HelloWorldSwift" target="_blank">Swift source code</a>

## Next Steps

From this page, you have learned how to create a simple video barcode decoding app. In the next steps, the following pages will help you on adding configurations to enhance your barcode reader.

- [Configure Runtime Settings](setting-guide.md)
- Additional Readings
  - <a href = "https://www.dynamsoft.com/barcode-types/barcode-types/" target = "_blank">Barcode Formats</a>

## Known Issues

### "dyld: Library not loaded" error on app initialization

You might run into this error in the app initialization phase - and in order to resolve this, a slight change needs to be done to the build settings of the project. Please make sure that you take the following steps to avoid this error:

- When adding the Barcode Reader framework in step 2 of the above instructions, make sure to tick off the **Copy items if needed** and **Create groups** options.
- In the **Build Settings** of the project, find the **Validate Workspace** setting and make sure it is set to **Yes**.
- In **General > Frameworks > Libraries and Embedded Content**, make sure that the **DynamsoftBarcodeReader.framework** is set to **Embed & Sign**.

### "Unsupported Architectures" error when building and releasing the application for the App Store

The error seems to stem from the inclusion of the **x86_64** architecture in **DynamsoftBarcodeReader.framework**. This error can potentially happen with dynamic libraries (like DBR iOS) that have pieces for all architectures, including devices and simulators. This error can be easily resolved by opting to use the **.xcframework** instead of the **.framework**. However, if you would like to keep using the **.framework**, please keep reading.

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
