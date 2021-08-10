---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Interface IntermediateResultCallback
description: This the interface IntermediateResultCallback page of Dynamsoft Barcode Reader for Android SDK.
keywords: IntermediateResultCallback, interface, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
---

# IntermediateResultCallback

The interface `IntermediateResultCallback` includes the abstract method(s) for users to operate on the intermediate results.

```java
interface com.dynamsoft.dbr.IntermediateResultCallback
```

| Method | Description |
| ------ | ----------- |
| `intermediateResultCallback` | The abstract class for users to get intermediate results from the callback. |

## intermediateResultCallback

The abstract class for users to get text result from the callback.

```java
void intermediateResultCallback(int var1, TextResult[] var2, Object var3);
```

**Parameters**

`frameId`: The ID of the frame.  
`results`: The intermediate result of the frame.
`userData`: Arguments passed to your function.

**Code Snippet**

```java
IntermediateResultCallback intermediateResultCallback = new IntermediateResultCallback() {
    @Override
    public void intermediateResultCallback(int frameID, IntermediateResult[] intermediateResult, Object userDate) {
        // Add your code
    }
};
```
