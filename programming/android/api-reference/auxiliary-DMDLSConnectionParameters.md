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

| Attributes | Type | Description |
|----------- | ---- | ----------- |
| [`mainServerURL`](#mainserverurl) | *String* | The URL of the license tracking server. |
| [`standbyServerURL`](#standbyserverurl) | *String* | The URL of the standby license tracking server. |
| [`handshakeCode`](#handshakecode) | *String* | The handshake code. |
| [`sessionPassword`](#sessionpassword) | *String* | The session password of the handshake code set in license tracking server. |
| [`uuidGenerationMethod`](#uuidgenerationmethod) | *int* | Sets the method to generate UUID. |
| [`maxBufferDays`](#maxbufferdays) | *int* | Sets the max days to buffer the license info. |
| [`limitedLicenseModules`](#limitedlicensemodules) | *int[]* | Sets the license modules to use. |
| [`chargeWay`](#chargeway) | *int* | Sets the charge way. |
| [`organizationID`](#organizationid) | *String* | The organization ID got from Dynamsoft. |

## mainServerURL

The URL of the license tracking server.

```java
String mainServerURL
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
String standbyServerURL
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
String handshakeCode
```

- **Value range**
    Any string value

- **Default value**
    null

## sessionPassword

The session password of the handshake code set in license tracking server.

```java
String sessionPassword
```

- **Value range**
    Any string value

- **Default value**
    null

## uuidGenerationMethod

Sets the method to generate UUID.

```java
int uuidGenerationMethod
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
int maxBufferDays
```

- **Value range**
    [7,0x7fffffff]  

- **Default value**
    7

## limitedLicenseModules

Sets the license modules to use.

```java
List<Integer> limitedLicenseModules
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
int chargeWay
```

- **Value range**
    Any one of the [`EnumDMChargeWay`]({{ site.enumerations }}other-enums.html#dm_chargeWay) Enumeration items.

## organizationID

The organization ID got from Dynamsoft.

```java
String organizationID
```

- **Value range**
    Any string value

- **Default value**
    ""
