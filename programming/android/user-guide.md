---
layout: default-layout
title: Dynamsoft Barcode Reader for Android - User Guide
description: This is the user guide of Dynamsoft Barcode Reader for Android SDK.
keywords: user guide, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
noTitleIndex: true
---


# Getting Started with Android

## Requirements

- Operating systems:
  - Supported OS: Android 5 or higher (Android 7 or higher recommended).
  - Supported ABI: armeabi-v7a, arm64-v8a, x86 and x86_64.

- Environment: Android Studio 3.4+.

## Installation

You can download the Dynamsoft Barcode Reader (DBR) SDK from the <a href="https://www.dynamsoft.com/barcode-reader/downloads/?utm_source=docs" target="_blank">Dynamsoft website</a> if you don't have the SDK installed yet.

After unzipping, the root directory of the DBR installation package is **DynamsoftBarcodeReader** (the `[INSTALLATION FOLDER]`). You can find the following two **aar** files under the **[INSTALLATION FOLDER]\Lib** directory:

| File | Description |
|---------|-------------|
| `DynamsoftBarcodeReaderAndroid.aar` | The Barcode Reader library, including all barcode decoding related algorithms and APIs. |
| `DynamsoftCameraEnhancerAndroid.aar` | The Camera Enhancer library, including camera control APIs and frame preprocessing algorithm.  |

## Build Your First Application

In this section, let's see how to create a HelloWorld app for reading barcodes from camera video input.

>Note:
>- Android Studio 4.2 is used here in this guide.
>- You can get the source code of the HelloWord app [here](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/HelloWorld).

### Create a New Project

1. Open Android Studio, select **File > New > New Project**.

2. Choose the correct template for your project. In this sample, we use **Empty Activity**.

3. When prompted, choose your app name 'HelloWorld' and set the **Save** location, **Language**, and **Minimum SDK** (we use 21 here).
    > Note: With **minSdkVersion** set to 21, your app is compatible with more than 94.1% of devices on the Google Play Store (last update: March 2021).

### Include the Library

There are two ways to include the SDK into your project - local binary dependency and remote binary dependency.

#### Local Binary Dependency

1. Copy the file `[INSTALLATION FOLDER]\Lib\DynamsoftBarcodeReaderAndroid.aar` and `[INSTALLATION FOLDER]\Lib\DynamsoftCameraEnhancerAndroid.aar` to the target directory `HelloWorld\app\libs`

2. Open the file `HelloWorld\app\build.gradle` and add reference in the dependencies:

    ```groovy
    dependencies {
        implementation fileTree(dir: 'libs', include: ['*.aar'])
    }
    ```

3. Click **Sync Now**. After the synchronization completes, the SDK is added to the project.

4. Import the package in the file `MainActivity.java`

   ```java
   import com.dynamsoft.dbr.*;
   import com.dynamsoft.dce.*;
   ```

<div class="fold-panel-prefix"></div>

#### Remote Binary Dependency <i class="fa fa-caret-down"></i>

<div class="fold-panel-start"></div>

1. Open the file `HelloWorld\app\build.gradle` and add the remote repository:

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

   > Note: Please replace {version-number} with the correct version number.

3. Click **Sync Now**. After the synchronization completes, the SDK is added to the project.

4. Import the package in the file `MainActivity.java`

   ```java
   import com.dynamsoft.dbr.*;
   import com.dynamsoft.dce.*;
   ```

<div class="fold-panel-end"></div>

### Initialize Camera Module

1. Create an instance of Camera Enhancer.

   ```java
   CameraEnhancer mCameraEnhancer;
   mCameraEnhancer = new CameraEnhancer(MainActivity.this);
   ```

2. In the Project window, open **app > res > layout > `activity_main.xml`** and create a DCE camera view section under the root node.

    ```xml
   <com.dynamsoft.dce.DCECameraView
      android:id="@+id/cameraView"
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      tools:layout_editor_absoluteX="25dp"
      tools:layout_editor_absoluteY="0dp" />
    ```

3. Initialize the camera view and bind to the Camera Enhancer object.

    ```java
    DCECameraView mCameraView;

    mCameraView = findViewById(R.id.cameraView);
    mCameraEnhancer.setCameraView(cameraView);
    ```

### Initialize Barcode Reader

1. Initialize the license.

   ```java
   BarcodeReader.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9", new DBRLicenseVerificationListener() {
      @Override
      public void DBRLicenseVerificationCallback(boolean isSuccess, Exception error) {
         if(!isSuccess){
             error.printStackTrace();
         }
      }
   });
   ```

2. Create an instance of Dynamsoft Barcode Reader.

   ```java
   BarcodeReader reader;
   reader = new BarcodeReader();
   ```

   >Note:
   >- Network connection is required for the license to work.
   >- The string "DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9" here will grant you a time-limited public trial license.
   >- If the license has expired, you can go to the <a href="https://www.dynamsoft.com/customer/license/trialLicense?utm_source=docs" target="_blank">customer portal</a> to request an extension.

3. Create text callback to obtain the recognized barcode results.

   ```java
   TextResultListener mTextResultListener = new TextResultListener() {
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

4. Set the text recognition callback and bind the camera to Barcode Reader object

   ```java
   // Bind the Camera Enhancer instance to the Barcode Reader instance.
   // The mCameraEnhancer is the instance of the Dynamsoft Camera Enhancer.
   // The Barcode Reader will use this instance to take control of the camera and acquire frames from the camera to start the barcode decoding process.
   reader.setCameraEnhancer(mCameraEnhancer);
   // The result will be an object that contains text result and other barcode information.
   try {
      reader.setTextResultListener(mTextResultListener, null);
   } catch (BarcodeReaderException e) {
      e.printStackTrace();
   }
   // Start the barcode scanning thread.
   reader.startScanning();
   ```

5. Override the `MainActivity.onResume` and `MainActivity.onPause` functions to start/stop video barcode scanning. After scanning starts, the Barcode Reader will automatically invoke the `decodeBuffer` API to process the video frames from the Camera Enhancer, then send the recognized barcode results to the text result callback.

   ```java
   @Override
   public void onResume() {
   // Start video barcode reading
      reader.startScanning();
      try {
         mCameraEnhancer.open();
      } catch (CameraEnhancerException e) {
         e.printStackTrace();
      }
      super.onResume();
   }

   @Override
   public void onPause() {
      // Stop video barcode reading
      reader.stopScanning();
      try {
         mCameraEnhancer.close();
      } catch (CameraEnhancerException e) {
         e.printStackTrace();
      }
      super.onPause();
   }
   ```

### Additional Steps

1. In the Project window, open **app > res > layout > `activity_main.xml`**, create a text view section under the root node to display the recognized barcode results.

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

### Build and Run the Project

1. Select the device that you want to run your app on from the target device drop-down menu in the toolbar.

2. Click the **Run app** button, then Android Studio installs your app on your connected device and starts it.

You can download the complete source code here:

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/HelloWorld" target="_blank">Android source code</a>

## Next Steps

From this page, you have learned how to create a simple video barcode decoding app. In the next steps, the following pages will help you on adding configurations to enhance your barcode reader.

- [Configure Runtime Settings](setting-guide.md)
- Additional Readings
  - <a href = "https://www.dynamsoft.com/barcode-types/barcode-types/" target = "_blank">Barcode Formats</a>
