---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - User Guide v8.4
description: This is the user guide of Dynamsoft Barcode Reader for Android SDK.
keywords: user guide v8.4, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---


# User Guide for Android Edition

- Systems Requirements:
  - Supported OS: Android 5 or higher (Android 7 or higher recommended)
  - Supported ABI: armeabi-v7a, arm64-v8a, x86 and x86_64

## Installation

To install Dynamsoft Barcode Reader for Android on your development machine, you can download the SDK from the [Dynamsoft website](https://www.dynamsoft.com/Downloads/Dynamic-Barcode-Reader-Download.aspx) and unzip `dbr-android-{version-number}.zip`.

After decompression, you can find samples in the **DBRSamples** folder under the **dbr-android-{version-number}** folder.

### Option 2: Build with Maven

You can add Dynamsoft Barcode Reader like below:

1. Add download URL in your project's `build.gradle`.

   ```java
    allprojects {
      repositories {
         google()
         jcenter()
         maven {
            url "http://download2.dynamsoft.com/maven/dbr/aar"
         }
      }
   }
   ```

2. Implement Dynamsoft Barcode Reader at dependencies in your module's `build.gradle`.

   ```java
   implementation 'com.dynamsoft:dynamsoftbarcodereader:{version-number}@aar'
   ```

   Please replace `{version-number}` with the correct version number, e.g.

   ```java
   implementation 'com.dynamsoft:dynamsoftbarcodereader:8.1.2@aar'
   ```

## Getting Started: HelloWorld

In this section, you will be guide on creating a Hello world app which can read barcodes from camera video input. `Dynamsoft Camera Enhancer` will be used to deploy the camera video input module in this guide.

### Create a New project and Include the Library

1. Create a new Android project in Android Studio.
2. Import the `DynamsoftBarcodeReaderAndroid.aar` and `DynamsoftCameraEnhancerAndroid.aar` files into the new project.

   To manually import the `.aar` :

      i. Decompress the `dbr-android-{version number}.zip` file and you will find `DynamsoftBarcodeReaderAndroid.aar` and `DynamsoftCameraEnhancerAndroid.aar` in the decompressed folder.
      ii. Put the .aar file under the directory libs in the project.
      iii. In the project, open `build.gradle(Module: app)` and add the following code:

      ```java
      repositories {
         flatDir {
            dirs 'libs'
         }
      }
      ```

      ii. Add `.aar` reference in the dependencies:

      ```java
      implementation(name: 'DynamsoftBarcodeReaderAndroid', ext: 'aar')
      implementation(name: 'DynamsoftCameraEnhancerAndroid', ext: 'aar')
      ```

      iii. Click **Sync Now**. After the synchronization completes, `DynamsoftBarcodeReaderAndroid.aar` and `DynamsoftCameraEnhancerAndroid.aar` are added to the project.

   Or you can use maven import the `.aar` file into the project.

      i. In the new project, open `build.gradle(module:app)` and add the following code:

      ```java
      allprojects {
         repositories {
            maven {
               url "http://download.dynamsoft.com/maven/dbr/aar"
               url "http://download.dynamsoft.com/maven/dce/aar"
            }
         }
      }
      ```

      ii. Then add `.aar` reference in the dependencies as below:

      ```java
      implementation 'com.dynamsoft:dynamsoftbarcodereader:{version number}@aar'
      implementation 'com.dynamsoft:dynamsoftcameraenhancer:{version number}@aar'
      ```

      iii. Click Sync Now. After the synchronization completes, `DynamsoftBarcodeReaderAndroid.aar` and `DynamsoftCameraEnhancerAndroid.aar` are added to the project.

### 

3. Add the following code to initiate and use the Dynamsoft Barcode Reader SDK.

    ```java
   import com.dynamsoft.dbr.BarcodeReader;
   import com.dynamsoft.dbr.BarcodeReaderException;
   import com.dynamsoft.dbr.DBRLTSLicenseVerificationListener;
   import com.dynamsoft.dbr.DCESettingParameters;
   import com.dynamsoft.dbr.TextResultCallback;
   import com.dynamsoft.dbr.TextResult;
   import com.dynamsoft.dce.CameraEnhancer;
   import com.dynamsoft.dce.CameraLTSLicenseVerificationListener;
   import com.dynamsoft.dce.CameraView;

   public class MainActivity extends AppCompatActivity {
      CameraView cameraView;            
      CameraEnhancer mCameraEnhancer;
      TextResultCallback mTextResultCallback;
      BarcodeReader reader;
      TextView tvRes;
      
      @Override
      protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);

            //Deploy the camera with Dynamsoft Camera Enhancer.
            cameraView = findViewById(R.id.cameraView);
            tvRes = findViewById(R.id.tv_res);
            mCameraEnhancer = new CameraEnhancer(MainActivity.this);
            mCameraEnhancer.addCameraView(cameraView);
            com.dynamsoft.dce.DMLTSConnectionParameters info = new com.dynamsoft.dce.DMLTSConnectionParameters();
            info.organizationID = "Put your organizationID here.";
            mCameraEnhancer.initLicenseFromLTS(info,new CameraLTSLicenseVerificationListener() {
               @Override
               public void LTSLicenseVerificationCallback(boolean isSuccess, Exception error) {
                  if(!isSuccess){ error.printStackTrace(); }
               }
            });
            mCameraEnhancer.setCameraDesiredState(CameraState.CAMERA_STATE_ON);
            mCameraEnhancer.startScanning();

            //Initialize Dynamsoft Barcode Reader from License Tracking Server.
            try {
               reader = new BarcodeReader();
               com.dynamsoft.dbr.DMLTSConnectionParameters parameters = new com.dynamsoft.dbr.DMLTSConnectionParameters();
               parameters.organizationID = "Put your organizationID here.";
               reader.initLicenseFromLTS(parameters, new DBRLTSLicenseVerificationListener() {
                  @Override
                  public void LTSLicenseVerificationCallback(boolean b, Exception e) {
                        if (!b) { e.printStackTrace(); }
                  }
               });
            } catch (BarcodeReaderException e) {
               e.printStackTrace();
            }
            //Get and display the text result.
            mTextResultCallback = new TextResultCallback() {
               @Override
               public void textResultCallback(int i, TextResult[] textResults, Object o) {
                  showResult(textResults);
               }
            };                
            //Set DCE setting parameters in Dynamsoft Barcode Reader.
            //The camera instance will be transferred as an argument to the barcode reader.
            //With the Camera instance, the barcode reader will automatically use decodeBuffer as the decode method.
            DCESettingParameters dceSettingParameters = new DCESettingParameters();
            dceSettingParameters._cameraInstance = mCameraEnhancer;
            dceSettingParameters._textResultCallback = mTextResultCallback;
            reader.SetCameraEnhancerParam(dceSettingParameters);
      }
      
      @Override
      public void onResume() {
            reader.StartCameraEnhancer();
            super.onResume();
      }

      @Override
      public void onPause() {
            reader.StopCameraEnhancer();
            super.onPause();
      }
      //This is the function for displaying decode result on the screen
      private void showResult(TextResult[] results) {
            if (results != null && results.length > 0) {
               String strRes = "";
               for (int i = 0; i < results.length; i++)
                  strRes += results[i].barcodeText + "\n\n";
               tvRes.setText(strRes);
            }
      }
   }
   ```

4. Run the project.

## Decoding Methods

The SDK provides multiple decoding methods that support reading barcodes from different sources, including static images, video stream, files in memory, base64 string, bitmap, etc. Here is a list of all decoding methods:

- [DecodeFile](api-reference/BarcodeReader/decode.md#decodefile): Reads barcodes from a specified file (BMP, JPEG, PNG, GIF, TIFF or PDF).
- [DecodeBase64String](api-reference/BarcodeReader/decode.md#decodebase64string): Reads barcodes from a base64 encoded string of a file.  
- [DecodeBitmap](api-reference/BarcodeReader/decode.md#decodebitmap): Reads barcodes from a bitmap. When handling multi-page images, it will only decode the current page.
- [DecodeBuffer](api-reference/BarcodeReader/decode.md#decodebuffer): Reads barcodes from raw buffer.
- [DecodeFileInMemory](api-reference/BarcodeReader/decode.md#decodefileinmemory): Decodes barcodes from an image file in memory.

You can find more samples in more programming languages at [Code Gallery](https://www.dynamsoft.com/Downloads/Dynamic-Barcode-Reader-Sample-Download.aspx) or [Github Repositories](https://github.com/dynamsoft-dbr?q=java&type=&language=).

## Barcode Reading Settings

Calling the [decoding methods](#decoding-methods) directly will use the default scanning modes and it will satisfy most of the needs. The SDK also allows you to adjust the scanning settings to optimize the scanning performance for different usage scenarios.

### Use [`PublicRuntimeSettings`](api-reference/class/PublicRuntimeSettings.md) class to Change Settings

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

```java
PublicRuntimeSettings runtimeSettings = reader.getRuntimeSettings();
//The barcode is set to OneD barcode.
runtimeSettings.barcodeFormatIds = 0x7FF;
//The barcode will try to find 10 barcodes.
runtimeSettings.expectedBarcodesCount = 10;
//The following code shrinks the decoding region by 25% on all sides
runtimeSettings.region.regionTop = 25;
runtimeSettings.region.regionBottom = 75;
runtimeSettings.region.regionLeft = 25;
runtimeSettings.region.regionRight = 75;
//The region is determined by the percentage
runtimeSettings.region.regionMeasuredByPercentage = 1;
reader.updateRuntimeSettings(runtimeSettings);
```
