---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Common Classes
description: This page shows the Common Classes of Dynamsoft Barcode Reader for Android SDK.
keywords: Common Classes, API reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
---

# Common Classes

## [iDBRPoint](auxiliary-iDBRPoint.md)

```objc
@interface iDBRPoint
```

The point class Stores the x and y coordinate of the points.

| Attribute | Type | Descriptions |
|---------- | ---- | ------------ |
| `x` | *NSInteger* | The X coordinate of the point. |
| `y` | *NSInteger* | The y coordinate of the point. |

## [iQuadrilateral](auxiliary-iQuadrilateral.md)

This class stores the quadrilateral points data.

```objc
@interface iQuadrilateral 
```  

| Attribute | Type | Descriptions |
|---------- | ---- | ------------ |
| `points` | *NSArray\** | Four vertexes in a clockwise direction of a quadrilateral. Index 0 represents the left-most vertex. |

## [iRegionDefinition](auxiliary-iRegionDefinition.md)

This class stores the region data. You can make settings on scan region through this class.

```objc
@interface iRegionDefinition
```  

| Attribute | Type | Descriptions |
|---------- | ---- | ------------ |
| [`regionTop`](#regiontop) | *NSInteger* | The top-most coordinate or percentage of the region. |
| [`regionLeft`](#regionleft) | *NSInteger* | The left-most coordinate or percentage of the region. |
| [`regionRight`](#regionright) | *NSInteger* | The right-most coordinate or percentage of the region. |
| [`regionBottom`](#regionbottom) | *NSInteger* | The bottom-most coordinate or percentage of the region. |
| [`regionMeasuredByPercentage`](#regionmeasuredbypercentage) | *NSInteger* | Sets whether or not to use percentage to measure the region size. |
