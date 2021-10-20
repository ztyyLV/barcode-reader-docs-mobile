---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - User Guide v8.8
description: This is the user guide of Dynamsoft Barcode Reader for Android SDK.
keywords: user guide v8.8, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---


# User Guide for Android Edition

## Requirements

- Operating systems:
  - Supported OS: Android 5 or higher (Android 7 or higher recommended).
  - Supported ABI: armeabi-v7a, arm64-v8a, x86 and x86_64.

- Environment: Android Studio 3.4+.

## Installation

If you don’t have SDK yet, please download the Dynamsoft Barcode Reader(DBR) SDK from the <a href="https://www.dynamsoft.com/barcode-reader/downloads/?utm_source=docs" target="_blank">Dynamsoft website</a> and unzip the package. After decompression, the root directory of the DBR installation package is `DynamsoftBarcodeReader`, which is represented by `[INSTALLATION FOLDER]`. You can also find the following two `aar` files in the `[INSTALLATION FOLDER]\Lib` directory: 

| File | Description |
|---------|-------------|
| `DynamsoftBarcodeReaderAndroid.aar` | The Barcode Reader library, includes all barcode decoding releated algorithms and APIs. |
| `DynamsoftCameraEnhancerAndroid.aar` | The Camera Enhancer library, includes camera control APIs and frame preprocessing algorithm.  |.

## Build Your First Application

In this section, you will be guided on creating a `HelloWorld` app that can read barcodes from camera video input.

>Note: 
>- The following steps are completed in Android Studio 4.2.
>- You can download the similar complete source code from [Here](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/HelloWorld).

### Create a New Project 

1. Open Android Studio and select New Project… in the File > New > New Project… menu to create a new project.

2. Choose the correct template for your project. In this sample, we’ll use `Empty Activity`.

3. When prompted, choose your app name (`HelloWorld`) and set the Save location, Language, and Minimum SDK (21)
    >Note: With minSdkVersion set to 21, your app is available on more than 94.1% of devices on the Google Play Store (last update: March 2021).

### Include the library

There are two ways to include the SDK into your project：

#### Local Binary Dependency

1. Copy the file `[INSTALLATION FOLDER]\Lib\DynamsoftBarcodeReaderAndroid.aar` and `[INSTALLATION FOLDER]\Lib\DynamsoftCameraEnhancerAndroid.aar` to the target directory `HelloWorld\app\libs`

2. Open the file `HelloWorld\app\build.gradle`, and add reference in the dependencies:
   
    ```groovy
    dependencies {
        implementation fileTree(dir: 'libs', include: ['*.aar'])
    }
    ```

3. Click `Sync Now`. After the synchronization completes, the SDK is added to the project.

4. import the package in the file `MainActivity.java`

   ```java
   import com.dynamsoft.dbr.*;
   import com.dynamsoft.dce.*;
   ```
   
#### Remote Binary Dependency

1. Open the file `HelloWorld\app\build.gradle`, and add the remote repository:
    
    ```groovy
    repositories {
         maven {
            url "https://download2.dynamsoft.com/maven/dbr/aar"
         }
         maven {
            url "https://download2.dynamsoft.com/maven/dce/aar"
         }
    }
    ```

2. Add reference in the dependencies:
   ```groovy
   dependencies {
      implementation 'com.dynamsoft:dynamsoftbarcodereader:{version-number}@aar'
      implementation 'com.dynamsoft:dynamsoftcameraenhancer:{version-number}@aar'
   }
   ```

   >Note:Please replace {version-number} with the correct version number.

3. Click `Sync Now`. After the synchronization completes, the SDK is added to the project.

4. import the package in the file `MainActivity.java`

   ```java
   import com.dynamsoft.dbr.*;
   import com.dynamsoft.dce.*;
   ```
    
### Initialize Camera Module

1. Initialize the license

   ```java
   CameraEnhancer.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9", new DCELicenseVerificationListener() {
      @Override
      public void DCELicenseVerificationCallback(boolean isSuccess, Exception error) {
         if(!isSuccess){
               error.printStackTrace();
         }
      }
   });
   ```    

   >Note:
   >- Network connection is required for the license to work.
   >- "DLS2***" is a default 7-day trial license used in the sample.
   >- If the license has expired, please request a trial license through the <a href="https://www.dynamsoft.com/customer/license/trialLicense?utm_source=docs" target="_blank">customer portal</a>.

2. Create an instance of Camera Enhancer

   ```java
   CameraEnhancer mCameraEnhancer;
   mCameraEnhancer = new CameraEnhancer(MainActivity.this);
   ```

3. In the Project window, open app > res > layout > `activity_main.xml`, create a DCE camera view section under the root node.

    ```xml
   <com.dynamsoft.dce.DCECameraView
      android:id="@+id/cameraView"
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      tools:layout_editor_absoluteX="25dp"
      tools:layout_editor_absoluteY="0dp" />
    ```

4. Initialize the camera view, and bind to the Camera Enhancer object.

    ```java
    DCECameraView mCameraView;

    mCameraView = findViewById(R.id.cameraView);
    mCameraEnhancer.setCameraView(cameraView);
    ```


### Initialize Barcode Reader

1. Create an instance of Dynamsoft Barcode Reader

   ```java
   BarcodeReader reader;
   reader = new BarcodeReader();
   ```

2. Initialize the license

   ```java
   DMDLSConnectionParameters dbrParameters = new DMDLSConnectionParameters();
   dbrParameters.organizationID = "200001";
   reader.initLicenseFromDLS(dbrParameters, new DBRDLSLicenseVerificationListener() {
         @Override
         public void DLSLicenseVerificationCallback(boolean isSuccessful, Exception e) {
            if (!isSuccessful) {
               e.printStackTrace();
            }
         }
   });
   ```    

   >Note:
   >- Network connection is required for the license to work.
   >- The organization id 200001 here will grant you a public trial license good for 7 days.
   >- If the license has expired, please request a trial license through the <a href="https://www.dynamsoft.com/customer/license/trialLicense?utm_source=docs" target="_blank">customer portal</a>.

3. Create text callback to obtain the recognized barcode results.

   ```java
   TextResultCallback mTextResultCallback = new TextResultCallback() {
   // Obtain the recognized barcode results and display.
   @Override
      public void textResultCallback(int i, TextResult[] textResults, Object userData) {
            (MainActivity.this).runOnUiThread(new Runnable() {
               @Override
               public void run() {
                  showResult(textResults);
               }
            });
      }
   };
   ```

4. Create settings of video barcode reading and bind to Barcode Reader object

   ```java
   // Create settings of video barcode reading.
   DCESettingParameters dceSettingParameters = new DCESettingParameters();

   // This cameraInstance is the instance of the Dynamsoft Camera Enhancer.
   // The Barcode Reader will use this instance to take control of the camera and acquire frames from the camera to start the barcode decoding process.
   dceSettingParameters.cameraInstance = mCameraEnhancer;

   // Make this setting to get the result. The result will be an object that contains text result and other barcode information.
   dceSettingParameters.textResultCallback = mTextResultCallback;

   // Bind the Camera Enhancer instance to the Barcode Reader instance.
   reader.SetCameraEnhancerParam(dceSettingParameters);
   ```

5. Override the MainActivity.onResume and MainActivity.onPause function to start/stop video barcode scanning. After start scanning, the Barcode Reader will automatically invoke the `decodeBuffer` API to process the video frames from the Camera Enhancer, then send the recognized barcode result to the text result callback.

   ```java
   @Override
   public void onResume() {
   // Start video barcode reading
      reader.StartCameraEnhancer();
      super.onResume();
   }

   @Override
   public void onPause() {
      // Stop video barcode reading
      reader.StopCameraEnhancer();
      super.onPause();
   }
   ```

### Additional Steps

1. In the Project window, open app > res > layout > `activity_main.xml`, create a text view section under the root node to display recognized barcode result.

   ```xml
    <TextView
        android:id="@+id/tv_res"
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:layout_marginTop="430dp"
        android:textSize="16sp"
        android:gravity="center"
        android:scrollbars="vertical"
        android:textColor="@color/white"
        android:visibility="visible"/>
   ```

2. Display barcode result in TextView.

   ```java
   TextView tvRes;

   // Add TextView to display recognized barcode results.
   tvRes = findViewById(R.id.tv_res);

   private void showResult(TextResult[] results) {
   if (results != null && results.length > 0) {
      String strRes = "";
      for (int i = 0; i < results.length; i++)
            strRes += results[i].barcodeText + "\n\n";
      tvRes.setText(strRes);
   } else {
      tvRes.setText("");
   }
   ```

You can download the similar complete source code from [Here](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/HelloWorld).

### Build and Run the Project

1. Select the device that you want to run your app on from the target device drop-down menu in the toolbar.

2. Click `Run app` button, then Android Studio installs your app on your connected device and starts it.


## Further Barcode Reading Settings

### Decoding Methods

The SDK provides multiple decoding methods that support reading barcodes from different sources, including static images, video stream, files in memory, base64 string, bitmap, etc. Here is a list of all decoding methods:

- [DecodeFile](api-reference/primary-decode.md#decodefile): Reads barcodes from a specified file (BMP, JPEG, PNG, GIF, TIFF or PDF).
- [DecodeBase64String](api-reference/primary-decode.md#decodebase64string): Reads barcodes from a base64 encoded string of a file.  
- [DecodeBitmap](api-reference/primary-decode.md#decodebitmap): Reads barcodes from a bitmap. When handling multi-page images, it will only decode the current page.
- [DecodeBuffer](api-reference/primary-decode.md#decodebuffer): Reads barcodes from raw buffer.
- [DecodeFileInMemory](api-reference/primary-decode.md#decodefileinmemory): Decodes barcodes from an image file in memory.

You can find more samples in more programming languages at [Code Gallery](https://www.dynamsoft.com/Downloads/Dynamic-Barcode-Reader-Sample-Download.aspx){:target="_blank"} or [Github Repositories](https://github.com/dynamsoft-dbr?q=java&type=&language=){:target="_blank"}.

Calling the [decoding methods](#decoding-methods) directly will use the default scanning modes and it will satisfy most of the needs. The SDK also allows you to adjust the scanning settings to optimize the scanning performance for different usage scenarios.

### [`PublicRuntimeSettings`](api-reference/auxiliary-PublicRuntimeSettings.md)

Here are some typical scanning settings you might find helpful:

- [Specify Barcode Type to Read](#specify-barcode-type-to-read)
- [Specify Maximum Barcode Count](#specify-maximum-barcode-count)
- [Specify a Scan Region](#specify-a-scan-region)

For more scanning settings guide, please read the [How To Guide]({{site.introduction}}how-to-guide/){:target="_blank"} section.

#### Specify Barcode Type to Read

A simple barcode format setting will result in a higher processing speed. By default, the SDK will read all the supported barcode formats except Postal Codes and Dotcode from the image. Please use the [`BarcodeFormatIds`]({{ site.enumerations }}format-enums.html#barcodeformat) and [`BarcodeFormat_2`]({{ site.enumerations }}format-enums.html#barcodeformat_2) to specify your barcode format(s) so that you can find the balance between speed and readability.

#### Specify maximum barcode count

By default, the SDK will try to find at least one barcode. You can use `expectedBarcodesCount` to specify the maximum number of barcodes. If you set the maximum number of barcodes n, the SDK will try to find at least n barcodes. The scanning process will not stop until n barcodes are found or timeout.

#### Specify a scan region

By default, the barcode reader will scan the whole image for barcodes. This can lead to poor performance, especially when dealing with high-resolution images. You can speed up the recognition process by restricting the scanning region.

**Code Snippet** of PublicRuntimeSettings

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
