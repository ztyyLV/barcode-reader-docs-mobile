---
layout: default-layout
title: Dynamsoft Barcode Reader Objective-C & Swift API Reference - License Methods
description: This page shows License methods of Dynamsoft Barcode Reader for iOS SDK.
keywords: initWithLicense, initWithLicenseFromServer, outputLicenseToString, license methods, api reference, objective-c, oc, swift
needAutoGenerateSidebar: true
noTitleIndex: true
---

# License Methods

  | Method               | Description |
  |----------------------|-------------|
  | [`initWithLicense`](#initwithlicense) | Initializes DynamsoftBarcodeReader with a license. |
  | [`initWithLicenseFromServer`](#initwithlicensefromserver) | Initialize license and connect to the specified server for online verification. |
  | [`outputLicenseToString`](#outputlicensetostring) | Outputs the license content as an encrypted string from the license server to be used for offline license verification. |
  | [`initLicenseFromLTS`](#initlicensefromlts) | Initializes the barcode reader license and connects to the specified server for online verification. |

  ---

## initWithLicense

Initializes DynamsoftBarcodeReader with a license.

```objc
- (instancetype _Nonnull)initWithLicense:(NSString* _Nonnull)license;
```

**Parameters**

`[in] license` The license key.

**Return Value**

The instance of DynamsoftBarcodeReader.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicense:@"t0260NwAAAHV***************"];
```
2. 
```swift
let barcodeReader = DynamsoftBarcodeReader.init(license: "t0260NwAAAHV***************")
```

## initWithLicenseFromServer

Initializes the license and connects to the specified server for online verification.

```objc
- (instancetype _Nonnull)initWithLicenseFromServer:(NSString* _Nullable)licenseSeServer licenseKey:(NSString* _Nonnull)licenseKey verificationDelegate:(id _Nullable)connectionDelegate;
```

**Parameters**

`[in] licenseSeServer` The name/IP of the license server.  
`[in] licenseKey` The license key.  
`[in,out] connectionDelegate` The delegate to handle callback when license server returns.

**Return Value**

The instance of DynamsoftBarcodeReader.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicenseFromServer:@"" licenseKey:@"C087****" verificationDelegate:self];

- (void)licenseVerificationCallback:(bool)isSuccess error:(NSError * _Nullable)error
{
    NSNumber* boolNumber = [NSNumber numberWithBool:isSuccess];
    dispatch_async(dispatch_get_main_queue(), ^{
    [self->verificationReceiver performSelector:self->verificationCallback withObject:boolNumber withObject:error];
    });
}
```
2. 
```swift
let barcodeReader = DynamsoftBarcodeReader(licenseFromServer: "", licenseKey: "C087****", verificationDelegate: self)

func licenseVerificationCallback(_ isSuccess: Bool, error: Error?)
{
    let boolNumber = NSNumber(value: isSuccess)
    DispatchQueue.main.async{
        self.verificationReceiver?.perform(self.verificationCallback!, with: boolNumber, with: error)
    }
}
```

## outputLicenseToString

Output the license content as an encrypted string from the license server to be used for offline license verification.

```objc
- (NSString *_Nullable)outputLicenseToString:(NSError* _Nullable * _Nullable)error;
```

**Parameters**

`[in,out] error` Input a pointer to an error object. If an error occurs, this pointer is set to an actual error object containing the error information. You may specify nil for this parameter if you do not want the error information.

**Return Value**

The output string which stores the contents of license.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
barcodeReader = [[DynamsoftBarcodeReader alloc] initWithLicenseFromServer:@"" licenseKey:@"C087****" verificationDelegate:self];
NSError __autoreleasing * _Nullable error;
[barcodeReader outputLicenseToString:&error];
```
2. 
```swift
let error: NSError? = NSError()
let barcodeReader = DynamsoftBarcodeReader(licenseFromServer: "", licenseKey: "C087****", verificationDelegate: self)
let licenseString = try? barcodeReader.outputLicenseToString()
```

## initLicenseFromLTS

Initializes the barcode reader license and connects to the specified server for online verification.

```objc
- (instancetype _Nonnull)initLicenseFromLTS:(iDMLTSConnectionParameters* _Nullable)ltsConnectionParameters verificationDelegate:(id _Nullable)connectionDelegate;
```

**Parameters**

`[in] ltsConnectionParameters` The struct DMLTSConnectionParameters with customized settings.  
`[in,out] connectionDelegate` The delegate to handle callback when license server returns.

**Return Value**

The instance of DynamsoftBarcodeReader.

**Code Snippet**

<div class="sample-code-prefix"></div>
>- Objective-C
>- Swift
>
>1. 
```objc
DynamsoftBarcodeReader *barcodeReader;
iDMLTSConnectionParameters* lts = [[iDMLTSConnectionParameters alloc] init];
lts.organizationID = @"200001";
lts.sessionPassword = @"******";
barcodeReader = [[DynamsoftBarcodeReader alloc] initLicenseFromLTS:lts verificationDelegate:self];
- (void)LTSLicenseVerificationCallback:(bool)isSuccess error:(NSError * _Nullable)error
{
        //TODO add your code for license verification
}
```
2. 
```swift
let lts = iDMLTSConnectionParameters()
lts.organizationID = "200001"
lts.sessionPassword = "******"
let barcodeReader = DynamsoftBarcodeReader(licenseFromLTS: lts, verificationDelegate: self)
func LTSLicenseVerificationCallback(_ isSuccess: Bool, error: Error?)
{
    print("isSucc : \(isSuccess) error : \(String(describing: error))")
}
```
