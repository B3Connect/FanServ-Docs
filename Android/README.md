# FanServer Android SDK Integration

1. [Introduction](#1-introduction)
2. [Configuration](#2-configuration)
3. [Show Ad For Screen](#3-show-ad-for-screen)
4. [Public Methods - Configuration Options](#4-public-methods---configuration-options)
  * [setAnimationStyle](#setanimationstyle)
  * [setBannerOutAnimationStyle](#setbanneroutanimationstyle)
  * [setWaitForImages](#setwaitforimages)
  * [setInterstitialOverridePendingTransition](#setinterstitialoverridependingtransition)
  * [setGps](#setgps)
  * [setAge](#setage)
  * [setGender](#setgender)
  * [setBannerAlign](#setbanneralign)
  * [setBannerMargin](#setbannermargin)
  * [resetBannerPosition](#resetbannerposition)
  * [setCheckDoubleAdShowOnResume](#setcheckdoubleadshowonresume)
  
## 1. Introduction

To work correctly the Ad server is required:

1. Library ad_server.jar.
1. Required entries in the AndroidMainfast.xml for activity:<br>
  `<activity android:name="com.b3connect.adserver.AdActivity" />` 
1. Required privileges in the AndroidManifest.xml:<br>
  `<uses-permission android:name="android.permission.INTERNET"/>`<br>
  `<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>`
1. Minimum API version: v8 Android 2.2 Froyo.

## 2. Configuration

For communication with the server is used for an object of class AdServer. AdServer is a singleton class. Reading is the class object through a static method:

```java
public static AdServer getInstance()
```

Before the first start advertising should configure the client giving app_ai and/or league by using one of the methods:
```java
public void init(String app_id)
```
```java
public void init(String app_id, String league)
```

## 3. Show Ad for screen

Displaying the ads in any activity carried out by calling one of the methods:

```java
public void startAd(Activity activity, String ad_type, String ad_size)
```

where `ad_type` and `ad_size` are one of the following values:

- B3AdTypeInterstitial : interstitial
  - B3AdSize320x480 : 320x480
  - B3AdSize480x800 : 480x800
  - B3AdSize640x960 : 640x960 
- B3AdTypeBanner : popup
  - B3AdSize300x50 : 300x150
  - B3AdSize320x50 : 320x150 
- B3AdTypeBanner : banner
  - B3AdSize300x50 : 300x50
  - B3AdSize320x50 : 320x50 
  - B3AdSize320x50 : 480x75 
  - B3AdSize320x50 : 640x100 
  - B3AdSize320x50 : 720x130 

```java
public void startAd(Activity activity)
```

This method of display advertising to the previously set values or default values: `B3AdTypeBanner` and `B3AdSize300x50`;

## 4. Public methods - configuration options

### setAnimationStyle

```java
public void setAnimationStyle(B3AdAnimation style)
```

Available enter animation style for banner:

- B3AdAnimationFromLeft
- B3AdAnimationFromRight
- B3AdAnimationFromTop
- B3AdAnimationFromBottom
- B3AdAnimationFadeIn

### setBannerOutAnimationStyle

```java
public void setBannerOutAnimationStyle(B3AdAnimation style)
```

Available exit animation style for banner:

- B3AdAnimationToLeft
- B3AdAnimationToRight
- B3AdAnimationToTop
- B3AdAnimationToBottom
- B3AdAnimationFadeOut

### setWaitForImages

```java
public void setWaitForImages(boolean wait)
```

In case when you are trying to show ad, but assets have not been downloaded yet, there are two possible solutions:

- `TRUE` - ad will be shown when assets downloading will finish.
- `FALSE` - ad will not be shown for this screen

### setInterstitialOverridePendingTransition

```java
public void setInterstitialOverridePendingTransition(int _enterAnim, int _exitAnim)
```

Method for setting the input and output of system animation interstitial ads

### setGps

```java
public void setGps(double latitude, double longitude)
```

Set gps position

### setAge

```java
public void setAge(int age)
```

Set user age

### setGender

```java
public void setGender(B3AdServer gender)
```

Set user gender

### setBannerAlign

```java
public void setBannerAlign(B3Align align)
```

Set banner position on the screen. Available  position:

- B3AlignLeft
- B3AlignCenter
- B3AlignRight
- B3AlignTopLeft
- B3AlignTopCenter
- B3AlignTopRight

### setBannerMargin

```java
public void setBannerMargin(int y)
```

Set banner margin from top (B3AlignTop...) or bottom (B3Align...)

### resetBannerPosition

```java
public void resetBannerPosition()
```

Reset baner position to default: B3AlignLeft and margin = 0  

### setCheckDoubleAdShowOnResume

```java
public void setCheckDoubleAdShowOnResume(boolean check)
```

Running an internal test of the advertising call one activity. (default: `TRUE`)

- `TRUE` - advertising activity automatically invokes the method onResume () - display the ads in the display window or the return of another activity.
- `FALSE` - calling multiple ads in one activity - call advertising inside the method OnCreate and / or events on the basis of inside activities.