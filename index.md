---
title: Doc Central
description: Home for Ezetap integration related documents
layout: default
type: Home
---

####Table of Contents####

1. Client Side
* Android SDK
* Windows SDK

2. Server Side
* Merchant Portal
* Notification API



## Client Side ##

Ezetap exposes client side SDKs to enable businesses to integrate `Ezetap POS` into their existing mobile, tablet or desktop applications via a standard SDK integration.

Ezetap SDK is available in the following platforms:

1. Android (``Android 2.2 or higher``)
2. Windows (``Windows 7 and 8.1``) 

Support for other platforms will be released shortly.

### Android SDK ###
Android SDK is available in the following two flavors to get your ideas implemented with Ezetap. You can choose whichever works for you!

####Hybrid JS ####

The simpler approach is to use HTML5 skills to make a web page and when you are ready to collect payment, call a simple Javascript function. This enables you to leverage full power of Google Chrome browser on the mobile or tablet. All you need is decent grasp of HTML, CSS and Javascript. It helps a lot if you are familiar with common libraries available on the client side. As far as Ezetap integration goes, all you need to do is to call one Javascript function when you are ready, with a JSON input.

Please visit [Android SDK - Hybrid JS]({{site.baseurl}}/pages/sdk-android-hybrid.html) home page for more details.

####Native Android ####

Second approach is to do native Android app development. Ezetap provides an SDK that you can integrate to your app. Naturally, this requires you to  have a good grasp of Android app development, building APKs etc. Ezetap integration involves setting up a project, importing a library and then actual coding involves few lines of code. Upside of this is that you get all features available on the native platform and you are not limited by the browser.

Please visit [Android SDK - Native]({{site.baseurl}}/pages/sdk-android-native.html) home page for more details.

### Windows SDK ###

On the Windows platform, Ezetap windows SDK is currently supported in Windows 7 and 8.1 versions. The SDK is  is implemented in C# and is available as a standard .NET library (version 4.5). It can be integrated into any existing .NET application as a DLL included as a project reference.

Please visit [Windows SDK]({{site.baseurl}}/pages/sdk-windows.html) home page for more details.

##Server Side##

###Merchant Portal###

Merchant portal gives you access to all the transactions posted on Ezetap server as well as other configurations related to merchants and users. Based on the user's role and access privilege, he or she can perform various activities on the transaction like void, refund etc. 

Please visit [Merchant Portal](#) home page for more details.

###Notification API###
Ezetap exposes a Notification API as a callback for customer's to receive notification of payment transactions (success or failure). This can be used for reconciling customer's backend systems with Ezetap payment transaction details. Any references passed to Ezetap SDK at the client end as part of a payment transaction will be sent in via the callback API as well.

Please visit [Notification API]({{site.baseurl}}/pages/api-notification.html) home page for more details.
