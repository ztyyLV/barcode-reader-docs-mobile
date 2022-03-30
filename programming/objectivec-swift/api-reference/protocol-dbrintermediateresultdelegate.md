---
layout: default-layout
title: Dynamsoft Barcode Reader iOS API Reference - DBRIntermediateResultListener
description: This page shows DBRIntermediateResultListener protocol of Dynamsoft Barcode Reader for iOS SDK.
keywords: DBRIntermediateResultListener, api reference, iOS
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# DBRIntermediateResultListener

The Protocol that handles callback when `IntermediateResult` is returned by the library.

```objc
@protocol DBRTextResultListener <NSObject>
```

| Method | Type | Description |
| ------ | ---- | ----------- |
| `intermediateResultCallback` | *required* | Represents the method to handle the intermediate result array returned by the library. |

## intermediateResultCallback

Represents the method to handle the intermediate result array returned by the library.

```objc
@required
- (void)intermediateResultCallback:(NSInteger)frameId imageData:(iImageData *_Nonnull)imageData results:(NSArray<iIntermediateResult*>* _Nullable)results;
```

**Parameters**

`frameID`: The ID of the frame.  
`imageData`: The image data of the frame.  
`results`: The intermediate results of the frame.
