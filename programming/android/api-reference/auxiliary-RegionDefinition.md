---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - RegionDefinition Class
description: This page shows the RegionDefinition Class of Dynamsoft Barcode Reader for Android SDK.
keywords: RegionDefinition, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---


# Class RegionDefinition

Stores the region information.

| Attribute | Type | Descriptions |
|---------- | ---- | ------------ |
| [`regionTop`](#regiontop) | *int* | The top-most coordinate or percentage of the region. |
| [`regionLeft`](#regionleft) | *int* | The left-most coordinate or percentage of the region. |
| [`regionRight`](#regionright) | *int* | The right-most coordinate or percentage of the region. |
| [`regionBottom`](#regionbottom) | *int* | The bottom-most coordinate or percentage of the region. |
| [`regionMeasuredByPercentage`](#regionmeasuredbypercentage) | *int* | Sets whether or not to use percentage to measure the region size. |

## regionTop

The top-most coordinate or percentage of the region.

```java
int regionTop
```

- **Value range**
    regionMeasuredByPercentage = 0: [0, 0x7fffffff]  
    regionMeasuredByPercentage = 1: [0, 100]  

- **Default value**
    0

## regionLeft

The left-most coordinate or percentage of the region.

```java
int regionLeft
```

- **Value range**
    regionMeasuredByPercentage = 0: [0, 0x7fffffff]  
    regionMeasuredByPercentage = 1: [0, 100]  

- **Default value**
    0

## regionRight

The right-most coordinate or percentage of the region.

```java
int regionRight
```

- **Value range**
    regionMeasuredByPercentage = 0: [0, 0x7fffffff]  
    regionMeasuredByPercentage = 1: [0, 100]  

- **Default value**
    0

## regionBottom

The bottom-most coordinate or percentage of the region.

```java
int regionBottom
```

- **Value range**
    regionMeasuredByPercentage = 0: [0, 0x7fffffff]  
    regionMeasuredByPercentage = 1: [0, 100]  

- **Default value**
    0

## regionMeasuredByPercentage

Sets whether or not to use percentage to measure the region size.

```java
int regionMeasuredByPercentage
```

- **Value range**
    [0, 1]

- **Default value**
    0

- **Remarks**
    When it's set to 1, the values of Top, Left, Right, Bottom indicate percentage (from 0 to 100); Otherwise, they indicate coordinates. 0: not by percentage 1: by percentage.
