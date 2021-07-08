---
layout: default-layout
title: Dynamsoft Barcode Reader Android API Reference - DMDLSConnectionParameters Class
description: This page shows the DMDLSConnectionParameters Class of Dynamsoft Barcode Reader for Android SDK.
keywords: DMDLSConnectionParameters, class, api reference, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---


# Class DMDLSConnectionParameters

Defines a struct to configure the parameters to connect to license tracking server.  

| Attributes | Type |
|---------- | ---- |
| [`mainServerURL`](#mainserverurl) | *String* |
| [`standbyServerURL`](#standbyserverurl) | *String* |
| [`handshakeCode`](#handshakecode) | *String* |
| [`sessionPassword`](#sessionpassword) | *String* |
| [`uuidGenerationMethod`](#uuidgenerationmethod) | *int* |
| [`maxBufferDays`](#maxbufferdays) | *int* |
| [`limitedLicenseModules`](#limitedlicensemodules) | *int[]* |
| [`chargeWay`](#chargeway) | *int* |
| [`organizationID`](#organizationid) | *String* |

## mainServerURL

The URL of the license tracking server.

```java
String com.dynamsoft.dbr.DMDLSConnectionParameters.mainServerURL
```

- **Value range**
    Any string value

- **Default value**
    null

- **Remarks**
    If you choose "Dynamsoft-hosting", then no need to change the value of MainServerURL and StandbyServerURL. When both are set to null (default value), it will connect to Dynamsoft's license tracking servers for online verification.

## standbyServerURL

The URL of the standby license tracking server.

```java
String com.dynamsoft.dbr.DMDLSConnectionParameters.standbyServerURL
```

- **Value range**
    Any string value

- **Default value**
    null

- **Remarks**
    If you choose "Dynamsoft-hosting", then no need to change the value of MainServerURL and StandbyServerURL. When both are set to null (default value), it will connect to Dynamsoft's license tracking servers for online verification.

## handshakeCode

The handshake code.

```java
String com.dynamsoft.dbr.DMDLSConnectionParameters.handshakeCode
```

- **Value range**
    Any string value

- **Default value**
    null

## sessionPassword

The session password of the handshake code set in license tracking server.

```java
String com.dynamsoft.dbr.DMDLSConnectionParameters.sessionPassword
```

- **Value range**
    Any string value

- **Default value**
    null

## uuidGenerationMethod

Sets the method to generate UUID.

```java
int com.dynamsoft.dbr.DMDLSConnectionParameters.uuidGenerationMethod
```

- **Value range**
    Any one of the [`EnumDMUUIDGenerationMethod`]({{ site.enumerations }}other-enums.html#dm_uuidgenerationmethod) Enumeration items.

- **Default value**
    DM_UUIDGM_RANDOM

- **See also**  
    [`EnumDMUUIDGenerationMethod`]({{ site.enumerations }}other-enums.html#dm_uuidgenerationmethod)

## maxBufferDays

Sets the max days to buffer the license info.

```java
int com.dynamsoft.dbr.DMDLSConnectionParameters.maxBufferDays
```

- **Value range**
    [7,0x7fffffff]  

- **Default value**
    7

## limitedLicenseModules

Sets the license modules to use.

```java
List<Integer> com.dynamsoft.dbr.DMDLSConnectionParameters.limitedLicenseModules
```

- **Value range**
    A list of the [`EnumDMLicenseModule`]({{ site.enumerations }}other-enums.html#dm_licensemodule) Enumeration items.

- **Default value**
    null

- **See also**  
    [`EnumDMLicenseModule`]({{ site.enumerations }}other-enums.html#dm_licensemodule)

## chargeWay

Sets the charge way.

```java
int com.dynamsoft.dbr.DMDLSConnectionParameters.chargeWay
```

- **Value range**
    Any one of the [`EnumDMChargeWay`]({{ site.enumerations }}other-enums.html#dm_chargeWay) Enumeration items.

## organizationID

The organization ID got from Dynamsoft.

```java
String com.dynamsoft.dbr.DMDLSConnectionParameters.organizationID
```

- **Value range**
    Any string value

- **Default value**
    ""
