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

## Build Your First Application

In this section, let's see how to create a HelloWorld app for reading barcodes from camera video input.

>Note:
>
>- Android Studio 4.2 is used here in this guide.
>- You can get the source code of the HelloWord app [here](https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/HelloWorld).

### Create a New Project

1. Open Android Studio, select **File > New > New Project**.

2. Choose the correct template for your project. In this sample, we use **Empty Activity**.

3. When prompted, choose your app name 'HelloWorld' and set the **Save** location, **Language**, and **Minimum SDK** (we use 21 here).
    > Note:
    >
    > - With **minSdkVersion** set to 21, your app is compatible with more than 94.1% of devices on the Google Play Store (last update: March 2021).

&nbsp;

### Add the SDK

There are two ways to add the SDK into your project - **Manually** and **Maven**.

#### Add the Library Manually

1. Download the SDK package from the <a href="https://www.dynamsoft.com/barcode-reader/downloads/?utm_source=docs" target="_blank">Dynamsoft website</a>. After unzipping, You can find the following **aar** files under the **DynamsoftBarcodeReader\Libs** directory:

   | File | Description |
   |---------|-------------|
   | `DynamsoftBarcodeReaderAndroid.aar` | The Barcode Reader library, including all barcode decoding related algorithms and APIs. |
   | `DynamsoftCameraEnhancerAndroid.aar` | The Camera Enhancer library, including camera control APIs and frame preprocessing algorithm.  |

2. Copy the above two **aar** files to the target directory `HelloWorld\app\libs`

3. Open the file `HelloWorld\app\build.gradle` and add reference in the dependencies:

    ```groovy
    dependencies {
        implementation fileTree(dir: 'libs', include: ['*.aar'])
    }
    ```

4. Click **Sync Now**. After the synchronization completes, the SDK is added to the project.
   >Note:
   >
   > - If your Android SDK version is 28 or higher, you have to add `android.enableJetifer=true` in your `gradle.properties` file before you sync your project with Gradle files.

#### Add the Library via Maven

1. Open the file `HelloWorld\app\build.gradle` and add the maven repository:

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
      implementation 'com.dynamsoft:dynamsoftbarcodereader:9.0.1@aar'
      implementation 'com.dynamsoft:dynamsoftcameraenhancer:2.1.3@aar'
   }
   ```

3. Click **Sync Now**. After the synchronization completes, the SDK is added to the project.
   >Note:
   >
   > - If your Android SDK version is 28 or higher, you have to add `android.enableJetifer=true` in your `gradle.properties` file before you sync your project with Gradle files.

&nbsp;

### Initialize License

1. Initialize the license in the file `MainActivity.java`.

   ```java
   import com.dynamsoft.dbr.BarcodeReader;
   import com.dynamsoft.dbr.DBRLicenseVerificationListener;
   
   public class MainActivity extends AppCompatActivity {

      @Override
      protected void onCreate(Bundle savedInstanceState) { 
         super.onCreate(savedInstanceState);
         setContentView(R.layout.activity_main);

         BarcodeReader.initLicense("DLS2eyJvcmdhbml6YXRpb25JRCI6IjIwMDAwMSJ9", new DBRLicenseVerificationListener() {
            @Override
            public void DBRLicenseVerificationCallback(boolean isSuccess, Exception error) {
               if(!isSuccess){
                  error.printStackTrace();
               }
            }
         });
      }
   }
   ```

   >Note:  
   >  
   >- Network connection is required for the license to work.
   >- The license string here will grant you a time-limited trial license.
   >- If the license has expired, you can go to the <a href="https://www.dynamsoft.com/customer/license/trialLicense?utm_source=docs" target="_blank">customer portal</a> to request for an extension.
   >- If you download the <a href="https://www.dynamsoft.com/barcode-reader/downloads/?utm_source=docs" target="_blank">installation package</a>, it comes with a 30-day trial license.

&nbsp;

### Initialize Camera Module

1. In the Project window, open **app > res > layout > `activity_main.xml`** and create a DCE camera view section under the root node.

   ```xml
   <com.dynamsoft.dce.DCECameraView
      android:id="@+id/cameraView"
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      tools:layout_editor_absoluteX="25dp"
      tools:layout_editor_absoluteY="0dp" />
    ```

2. Import the dynamsoft camera module, initialize the camera view and bind to the created Camera Enhancer instance in the file `MainActivity.java`.

   ```java
   ...
   
   import com.dynamsoft.dce.DCECameraView;
   import com.dynamsoft.dce.CameraEnhancer;
   import com.dynamsoft.dce.CameraEnhancerException;

   public class MainActivity extends AppCompatActivity {
      CameraEnhancer mCameraEnhancer;

      @Override
      protected void onCreate(Bundle savedInstanceState) { 

         ...
         // Add camera view for previewing video.
         DCECameraView cameraView = findViewById(R.id.cameraView);

         mCameraEnhancer = new CameraEnhancer(MainActivity.this);
         mCameraEnhancer.setCameraView(cameraView);
      }
   }
   ```

&nbsp;

### Initialize Barcode Reader

1. Import and initialize the barcode reader, bind to the created Camera Enhancer instance.

   ```java
   ...

   import com.dynamsoft.dbr.BarcodeReaderException;

   public class MainActivity extends AppCompatActivity {
      
      ...

      BarcodeReader mReader;

      @Override
      protected void onCreate(Bundle savedInstanceState) { 
         
         ...

         try {
            mReader = new BarcodeReader();
         } catch (BarcodeReaderException e) {
            e.printStackTrace();
         }

         mReader.setCameraEnhancer(mCameraEnhancer);
      }
   }
   ```

2. Create a barcode result listener and register with the barcode reader instance to get recognized barcode results.

   ```java
   ...

   import com.dynamsoft.dbr.ImageData;
   import com.dynamsoft.dbr.TextResult;
   import com.dynamsoft.dbr.TextResultListener;

   public class MainActivity extends AppCompatActivity {
      
      @Override
      protected void onCreate(Bundle savedInstanceState) { 
         
         ...
         mReader.setTextResultListener(new TextResultListener() {
            // Obtain the recognized barcode results and display.
            @Override
               public void textResultCallback(int id, ImageData imageData, TextResult[] textResults) {
                     (MainActivity.this).runOnUiThread(new Runnable() {
                        @Override
                        public void run() {
                           showResult(textResults);
                        }
                     });
               }
         });
      }
   }
   ```

3. Override the `MainActivity.onResume` and `MainActivity.onPause` functions to start/stop video barcode scanning. After scanning starts, the Barcode Reader will automatically invoke the `decodeBuffer` API to process the video frames from the Camera Enhancer, then send the recognized barcode results to the text result callback.

   ```java
   public class MainActivity extends AppCompatActivity {
      
      ...

      @Override
      public void onResume() {
         // Start video barcode reading
         mReader.startScanning();
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
         mReader.stopScanning();
         try {
            mCameraEnhancer.close();
         } catch (CameraEnhancerException e) {
            e.printStackTrace();
         }
         super.onPause();
      }
   }
   ```

&nbsp;

### Additional Steps

1. In the Project window, open **app > res > layout > `activity_main.xml`**, create a text view section under the root node to display the recognized barcode results. The following sample code is a TextView under RelativeLayout

   ```xml
   ...
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
   public class MainActivity extends AppCompatActivity {
      
      ...
      TextView tvRes;

      @Override
      protected void onCreate(Bundle savedInstanceState) {
         ...
         
         // Add TextView to display recognized barcode results.
         tvRes = findViewById(R.id.tv_res);
      }

      private void showResult(TextResult[] results) {
         if (results != null && results.length > 0) {
            String strRes = "";
            for (int i = 0; i < results.length; i++)
                  strRes += results[i].barcodeText + "\n\n";
            tvRes.setText(strRes);
         } else {
            tvRes.setText("");
         }
      }
   }
   ```

&nbsp;

### Build and Run the Project

1. Select the device that you want to run your app on from the target device drop-down menu in the toolbar.

2. Click the **Run app** button, then Android Studio installs your app on your connected device and starts it.

You can download the complete source code here:

- <a href="https://github.com/Dynamsoft/barcode-reader-mobile-samples/tree/main/android/HelloWorld" target="_blank">Android source code</a>

## Next Steps

From this page, you have learned how to create a simple video barcode decoding app. In the next steps, the following pages will help you on adding configurations to enhance your barcode reader.

- [Add Basic Settings](add-basic-settings.md)
- [Add UI Settings](ui-configurations.md)
- [Optimize Performance](quick-performance-settings.md)
- Additional Readings
  - <a href = "https://www.dynamsoft.com/barcode-types/barcode-types/" target = "_blank">Barcode Formats</a>
