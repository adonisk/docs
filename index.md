---
title: Document Center
---

# Ezetap Extensibility Framework #

Ezetap Extensibility Framework is aimed at enabling businesses to leverage the capabilities of Ezetap's mPOS system to manage Card, Cash and Cheque payments, easily integrated into their existing mobile, tablet and desktop applications via a standard SDK integration.

Ezetap SDK is available in the following platforms:

1. Android (``Android 2.2 or higher``)
2. Windows (``Windows 7 and 8.1``) 

Support for other platforms will be released shortly.

## Android SDK ##


There are two ways to get started with implementing your ideas with Ezetap on the Android platform. You can choose whichever works for you!

**Web View ( HTML5 )**

The simpler approach is to use HTML5 skills to make a web page and when you are ready to collect payment, call a simple Javascript function. This enables you to leverage full power of Google Chrome browser on the mobile or tablet. All you need is decent grasp of HTML, CSS and Javascript. It helps a lot if you are familiar with common libraries available on the client side. As far as Ezetap integration goes, all you need to do is to call one Javascript function when you are ready, with a JSON input.

For more details on [Android - HTML5 UI integration](#!android-html5.md)

**Native App Integration**

Second approach is to do native Android app development. Ezetap provides an SDK that you can integrate to your app. Naturally, this requires you to  have a good grasp of Android app development, building APKs etc. Ezetap integration involves setting up a project, importing a library and then actual coding involves few lines of code. Upside of this is that you get all features available on the native platform and you are not limited by the browser.

For more details on [Android - SDK integration](#!android-sdk.md)

## Windows SDK ##

Windows SDK is currently supported in Windows 7 and 8.1 versions. The SDK is  is implemented in C# and is available as a standard .NET library (version 4.5). It can be integrated into existing .NET application as a DLL included as a project reference.

For more details on [Windows - SDK integration](#!windows-sdk.md)