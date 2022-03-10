---
layout: default-layout
title: Dynamsoft Barcode Reader for Objective-C & Swift - How to Upgrade
description: This is the how to upgrade of Dynamsoft Barcode Reader for iOS SDK.
keywords: How to upgrade, objective-c, oc, swift
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
pageStartVer: 8.0
---

# How to Upgrade

## From Version 8.x to 9.x

### Update the SDK to 9.x Version

If you are referencing the library from local file:

- Replace the old `DynamsoftBarcodeReaderAndroid.aar` and `DynamsoftCameraEnhancerAndroid.aar` file with the one in the latest version.

If you are using Maven

- Change the version number to v9.x in `app\build.gradle` file.

### Update the License Activation Code

If you were using the following license activation APIs:

Objective-C:

```objc
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicense:@"An offline license"];
```

```objc
_barcodeReader = [[DynamsoftBarcodeReader alloc] initLicenseFromDLS:DLSConnectionPara verificationDelegate:self];
- (void)DLSLicenseVerificationCallback:(bool)isSuccess error:(NSError * _Nullable)error{

}
```

Swift:

```swift
let barcodeReader = DynamsoftBarcodeReader.init(license: "An offline license")
```

```swift
barcodeReader = DynamsoftBarcodeReader(licenseFromDLS: DLSConnectionPara, verificationDelegate: self)
func DLSLicenseVerificationCallback(_ isSuccess: Bool, error: Error?){

}
```

Please replace your license activation code with the following code. You can get the `3.0 license` from [customer portal-->License detail](#update-the-license-activation-code).

Objective-C:

```objc
[DynamsoftBarcodeReader initLicense:@"Put your license here" verificationDelegate: self];
- (void)DBRLicenseVerificationCallback:(bool)isSuccess error:(NSError *)error{

}
```

Swift:

```Swift
DynamsoftBarcodeReader.initLicense("Put your license here", verificationDelegate: self)
func dbrLicenseVerificationCallback(_ isSuccess: Bool, error: Error?) {

}
```

> Note:
> The following license activation methods are deprecated:
>
> - `initLicenseFromDLS`
> - `initLicenseFromServer`
> These methods will be removed in 10.0 release. You don't have to make the changes in 9.x upgrade.

### Update the Video Barcode Decoding Code

Some of the legacy video barcode decoding methods are deprecated. Make sure to change your code if you were using the following APIs:

- Legacy Frame Decoding APIs:
  - `interface iFrameDecodingParameters`
  - `protocol DBRErrorDelegate`
  - `BarcodeReader.startFrameDecoding`
  - `BarcodeReader.startFrameDecodingEx`
  - `BarcodeReader.appendFrame`
  - `BarcodeReader.setDBRErrorDelegate`
  - `BarcodeReader.stopFrameDecoding`
  - `BarcodeReader. getFrameDecodingParameters`
  - `BarcodeReader.getLengthOfFrameQueue`

- Legacy Camera Enhancer supporting APIs
  - interfance `iDCESettingParameters`
  - `BarcodeReader.setCameraEnhancerPara`

> Note:
>
> If you are upgrading from v8.9.0 or higher versions, you might not need to make any changes on video barcode decoding APIs.

### Update Swift Code

We made quit a lot of changes on the Swift APIs in 9.0 version. Please check the API documents for the details if you are using the following APIs.

- Modified Swift APIs
  - The following method names are changed:
    - `DynamsoftBarcodeReader.updateRuntimeSettings`(with parameter `iPublicRuntimeSettings`)
    - `DynamsoftBarcodeReader.decodeIntermediateResult`
    - `DynamsoftBarcodeReader.decodeImage`
    - `DynamsoftBarcodeReader.decodeFileWithName`
    - `DynamsoftBarcodeReader.initRuntimeSettingsWithFile`
    - `DynamsoftBarcodeReader.initRuntimeSettingsWithString`
    - `DynamsoftBarcodeReader.appendTplFileToRuntimeSettings`
    - `DynamsoftBarcodeReader.appendTplStringToRuntimeSettings`
    - `DynamsoftBarcodeReader.outputSettingsToString`
    - `DynamsoftBarcodeReader.outputSettingsToFile`
  - The following methods will signal errors by returning NSErrors
    - `DynamsoftBarcodeReader.getIntermediateResult`
    - `DynamsoftBarcodeReader.createIntermediateResult`
    - `DynamsoftBarcodeReader.outputLicenseToString`
    - `DynamsoftBarcodeReader.outputSettingsToString`
    - `DynamsoftBarcodeReader.allParameterTemplateNames`
    - `DynamsoftBarcodeReader.getModeArgument`
    - `DynamsoftBarcodeReader.getRuntimeSettings`
  - The following methods will signal errors by throw exceptions
    - `DynamsoftBarcodeReader.decodeIntermediateResult`
    - `DynamsoftBarcodeReader.decodeImage`
    - `DynamsoftBarcodeReader.decodeFileWithName`
    - `DynamsoftBarcodeReader.decodeBase64`
    - `DynamsoftBarcodeReader.decodeBuffer`
  - The following methods will return an BOOL value
    - `DynamsoftBarcodeReader.updateRuntimeSettings`
    - `DynamsoftBarcodeReader.setModeArgument`
    - `DynamsoftBarcodeReader.resetRuntimeSettings`
    - `DynamsoftBarcodeReader.initRuntimeSettingsWithFile`
    - `DynamsoftBarcodeReader.initRuntimeSettingsWithString`
    - `DynamsoftBarcodeReader.appendTplFileToRuntimeSettings`
    - `DynamsoftBarcodeReader.appendTplStringToRuntimeSettings`
    - `DynamsoftBarcodeReader.outputSettingsToFile`

## From Version 8.0 to 8.x

You need to replace the old `DynamsoftBarcodeReader.framework` file with the one in the latest version. Download the latest version [here](https://www.dynamsoft.com/Downloads/Dynamic-Barcode-Reader-Download.aspx). You could also download it via terminal `pod install ‘DynamsoftBarcodeReader’`. For v8.9 or higher v8.x versions, you have to include `DynamsoftCameraEnhancer.framework` as well.

## From Version 7.x to 8.x

You need to replace the old `DynamsoftBarcodeReader.framework` file with the one in the latest version. Download the latest version [here](https://www.dynamsoft.com/Downloads/Dynamic-Barcode-Reader-Download.aspx).

Your previous SDK license for version 7.x is not compatible with version 8.x. Please [contact us](https://www.dynamsoft.com/Company/Contact.aspx) to upgrade your license.

In v8.0, we introduced a new license tracking mechanism, <a href="https://www.dynamsoft.com/license-tracking/docs/about/index.html" target="_blank">License 2.0</a>.

If you wish to use License 2.0, please refer to [this article](../../license-activation/set-full-license.md) to set the license.

After you upgraded your license to version 8.x:

- If you were using `initWithLicense`, please replace the old license with the newly generated one.

- If you were using `initWithLicenseFromServer` to connect to the Dynamsoft server for license verification, then no need to change the license key. But please make sure the device has an Internet connection.

## From Version 6.x to 8.x

We made some structural updates in the new version. To upgrade from 6.x to 8.x, we recommend you to review our sample code and re-write the barcode scanning module.
