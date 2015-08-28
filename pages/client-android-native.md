---
title: Android - Native
description: Integrating a native app using Android SDK
type: Client Side
layout: default
---

This section is meant for people who have existing android native apps and would like to integrate Ezetap PoS solution through a native android SDK implementation. 

> **Note:** If you are looking for a standalone PoS solution for Android mobile or tablet, please refer to the `Ezetap Android PoS` documentation

#### What you need to get started####

	1. Android development environment
	2. Android phone that can connect to internet
	3. This documentation
	4. Ezetap app key or login credentials to Ezetap service
	5. Ezetap device to test

##[Download SDK]({{site.base_url}}/downloads/client-sdk/android/ezetap_sdk_android_2_0_8.zip)##

You can download the latest version of Ezetap Android SDK by clicking the link above. Ezetap support team will set up and communicate with the necessary Merchant account, AppKey and other details for you.

###Package Components###

The Ezetap SDK package consists of the following components.

* The Ezetap SDK package contains the following:
  1. `ezetap_sdk_2_0_buildnumber.jar` : This jar contains the necessary binaries required to integrate Ezetap Payment into your application. This jar is to be added into the libs directory of your Android application.
  1. `ezetap_sdk_sample_code_2_0_buildnumber.zip` : This archive file contains an Android app sample that demonstrates the usage of the Ezetap SDK.
  1. `ezetap_sdk_2_0_buildnumber.buildnumber` : an empty marker file denoting the version number and build number of the Ezetap SDK.
  1. [`javadoc`](javadoc/index.html) :  A directory containing developer documentation in Javadoc format for the Ezetap APIs available, using which integration is to be done.
* A document containing *AppKey* and other *ORG* specific information for your organization.
* `Ezetap Android SDK Implementation Guide` : this document.

### Setting up your Development Environment###
Upon receiving the Ezetap SDK package, unzip the contents into a directory of choice. Add `ezetap_sdk_2_0_buildnumber.jar` to the `libs` directory of your Android Project.

![image]({{site.baseurl}}/images/eclipse-sdk-layout.png)

You are now ready to invoke Ezetap APIs using which you can integrate Ezetap's Card, Cash and other capabilities into your application.

## Ezetap APIs - [Complete API Reference]({{site.baseurl}}/api-docs/android/native/index.html)
This section gives a brief introduction to the APIs available as part of the Ezetap SDK.

  | Name                                                             | Meaning                                                                                                                                                                                                                                                                  |
  | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
  | [`EzetapApiConfig`](javadoc/com/ezetap/sdk/EzetapApiConfig.html) | This is the basic Config object to be used for creating a handle to the `EzetapPayApi`. A populated instance of this class, containing your org-specific settings/params is to be used to obtain a handle to the `EzetapPayApi`, using which you may invoke Ezetap APIs. |
  | [`EzetapPayApis`](javadoc/com/ezetap/sdk/EzetapPayApis.html)     | Calling `create()` or `create(EzetapApiConfig)` creates and returns a handle to `EzetapPayApi`.  This may be used to invoke Ezetap APIs.                                                                                                                                 |
  | [`EzetapPayApi`](javadoc/com/ezetap/sdk/EzetapPayApi.html)       | Upon getting a handle to an instance of this class using the above APIs, you may invoke Ezetap APIs                                                                                                                                                                      |


Note: Please refer to the [complete API Javadoc]({{site.baseurl}}/api-docs/android/native/index.html) provided as part of the Ezetap SDK package to
learn more about the Ezetap APIs. The accompanied sample code contains examples to help understand how to invoke the Ezetap APIs.

## Handling Responses

All Ezetap APIs respond with the follwing result codes

  | Result Code                   | Meaning                                    |
  | ----------------------------- | ------------------------------------------ |
  | `EzeConstants.RESULT_SUCCESS` | Value = 2001 Indicates SUCCESS of API call |
  | `EzeConstants.RESULT_FAILED`  | Value = 3001 Indicates FAILURE             |


In cases where the API returns data to the calling application, the `Intent` returned will contain the JSON response. This JSON may be 
retrieved as a `String Extra` from the `Intent`, using the key `EzeConstants.KEY_RESPONSE_DATA` and parsed into a `JSONObject`. The JSON contains the following.

  | Result           | Meaning                                                                                                           |
  | ---------------- | ----------------------------------------------------------------------------------------------------------------- |
  | success          | Value = true or false. True indicating success of API and false indicating failure                                |
  | errorCode        | Value = ezetap_error_code. This is to be quoted to Ezetap Support whilst communicating any issue.                 |
  | errorMessage     | Value = A description of the error This is to be quoted to Ezetap Support in conjunction with the errorCode above |


Hint: For Transaction APIs, you may create an instance of [`TransactionDetails`]({{site.baseurl}}/api-docs/android/native/com/ezetap/sdk/TransactionDetails.html) using the JSON data for ease of use.


## Updating Ezetap Service App
Access to the Ezetap APIs is provided and facilited by the Ezetap Service App. The Ezetap SDK provides the API interface 
necessary to call Ezetap APIs via the Service App. As and when Ezetap rectifies issues and enhances the Service App, updates are made available to Ezetap SDK users.

It is recommended that calling apps periodically check for updates and stay current by calling the [checkForUpdate]({{site.baseurl}}/api-docs/android/native/com/ezetap/sdk/EzetapPayApi.html#checkForUpdate) API provided by the Ezetap SDK. You may transform the JSON response into an instance of [`EzetapAppUpdateResponse`]({{site.baseurl}}/api-docs/android/native/com/ezetap/sdk/EzetapAppUpdateResponse.html) and based on the severity of the update, choose to update. The Service App may be updated by creating an instance of [`EzetapDownloadUtils`]({{site.baseurl}}/api-docs/android/native/com/ezetap/sdk/EzetapDownloadUtils.html) and calling `start()`. This will download the latest service app and update it on the mobile device.


	void checkForUpdate(Activity context, int reqCode, String username);

> Use this API to check if there is an update to the Ezetap Service App. It is recommended that this API be called by application implementations periodically. For example, you may choose to call this API at application start time or at login time.

### EzetapAppUpdateResponse
A bean representation of the response from the Ezetap server to the `checkForUpdate` API call. Please refer to the [javadoc]({{site.baseurl}}/api-docs/android/native/index.html) to know more about the attributes available.

### EzetapDownloadUtils
Provides utilities to download and install updates to the Ezetap Service App. Create an instance of [`EzetapDownloadUtils`]({{site.baseurl}}/api-docs/android/native/com/ezetap/sdk/EzetapDownloadUtils.html) and call the `start()` method. This will initiate the download and prompt the user to update, if one is found.

## Incomplete Transactions

The Ezetap Service App and SDK combination provides for handling of incomplete transactions and transactions for which no response is received.  Failure to receive a response may occur due to

* a time out on the mobile device, wherein no response is received and there is no knowledge of whether the transaction succeeded or not
* a network outage on the mobile device because of which the response was not received, although the request did go through
* any other environmental condition/reason preventing the mobile device from receiving a response from the server

In the above cases, the Ezetap Service app prompts the user with a message `Response Not Received` and provides the user with ability to `Retrieve Transaction`. If the transaction was a success, the user may complete it as part of the normal flow and obtain the customer's signature to complete the transaction. If there was a failure in the transaction, the user is informed accordingly and may proceed to retry the transaction.  Incomplete transactions may occur due to

* an application crash
* inadvertant app closure
* inadvertantly hitting the back button when the transaction may already have reached Ezetap

In all the above cases, the Ezetap service app prompts the user that an `Incomplete Transaction` has been detected. The user is expected to tap `Retrieve Transaction` to check the status of the transaction and retrieve it. The user can then complete it, in case of transaction success and obtain the customer's signature.  The Ezetap SDK also provides an API that calling applications may choose to call at any time to check for and go through the process for an incomplete transaction, if found.

	void checkForIncompleteTransaction(Activity context, int reqCode, String username);

>  Use this API to check if there is an incomplete transaction. Any card transaction that was initiated, but failed to receive a response due to any of the conditions listed above will be detected and the user will be guided through the steps to complete the transaction.

### Recommendation

Ezetap strongly recommends that application implementations leverage the use of the above API to check for any incomplete previous transactions.

This is especially important in cases where Ezetap is primarily used for Card payments only. While the check for an incomplete transaction will detect any pending incomplete transactions, it will do so ONLY when Ezetap APIs are invoked. To alleviate any anomalies, application implementations are strongly recommended to implement this API call at appropriate points in the app flow, for example: 

* at application login time
* at application lauch time
* in cases where Cash is handled outside of the Ezetap system, at the time when Cash is chosen as a payment option


## Typical API Usage

All these APIs below are in [`EzetapPayApi`]({{site.baseurl}}/api-docs/android/native/com/ezetap/sdk/EzetapPayApi.html).

  | API                     | Usage                                                                                                                                                                                                                                                                                                                               |
  | ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
  | `initializeDevice`      | To initialize device and authenticate it with bank. It is recommended that this API is used every day in the morning as a routine. If this API call is missed then the initilaization of the device will happen during the first transaction of the day. Typically this API is used through a menu item in application home screen. |
  | `startCardPayment`      | To perform card payment.                                                                                                                                                                                                                                                                                                            |
  | `getTransactionHistory` | To fetch the transaction history of the user.                                                                                                                                                                                                                                                                                       |
  | `startVoidTransaction`  | To perform void on existing unsettled transaction.                                                                                                                                                                                                                                                                                  |

