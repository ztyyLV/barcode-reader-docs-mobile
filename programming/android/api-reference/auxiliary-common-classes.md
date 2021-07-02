---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - Common Classes
description: This page shows the Common Classes of Dynamsoft Barcode Reader for Android SDK.
keywords: Common Classes, API reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: false
---

# Common Classes

## [Point](auxiliary-Point.md)

```java
import com.dynamsoft.dbr.Point;
```

The point class Stores the x and y coordinate of the points.

| Attribute | Type | Descriptions |
|---------- | ---- | ------------ |
| `x` | *int* | The X coordinate of the point. |
| `y` | *int* | The y coordinate of the point. |

## [Quadrilateral](auxiliary-Quadrilateral.md)

This class stores the quadrilateral points data.

```java
import com.dynamsoft.dbr.Point;
```

| Attribute | Type | Descriptions |
|---------- | ---- | ------------ |
| [`points`](#points) | [`Point`](Point.md)[] | Four vertexes in a clockwise direction of a quadrilateral. Index 0 represents the left-most vertex. |

## [RegionDefinition](auxiliary-RegionDefinition.md)

This class stores the region data. You can make settings on scan region through this class.

```java
import com.dynamsoft.dbr.RegionDefinition;
```

| Attribute | Type | Descriptions |
|---------- | ---- | ------------ |
| [`regionTop`](#regiontop) | *int* | The top-most coordinate or percentage of the region. |
| [`regionLeft`](#regionleft) | *int* | The left-most coordinate or percentage of the region. |
| [`regionRight`](#regionright) | *int* | The right-most coordinate or percentage of the region. |
| [`regionBottom`](#regionbottom) | *int* | The bottom-most coordinate or percentage of the region. |
| [`regionMeasuredByPercentage`](#regionmeasuredbypercentage) | *int* | Sets whether or not to use percentage to measure the region size. |
