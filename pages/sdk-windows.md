---
title: 4. Windows SDK
description: Integrating a windows application using Ezetap .NET sdk
type: Client SDK
layout: default
---

##Introduction##

This section is for people who have existing windows (ver 7 or 8.1) applications running on a desktop and planning to integrate Ezetap mPoS solution using a standard windows SDK.

> **Note:** If you are looking for a standalone mPoS solution for windows desktop or tablet, please refer to the ``Ezetap Basic mPoS (for windows)`` documentation
 
 
####What do you need to get started####

	1. A Visual Studio .NET development environment
	2. A Windows tablet / desktop (with a connection to internet) to test the application 
	3. A DEMO merchant setup and login credentials to Ezetap service
	4. Ezetap device connected to the tablet / desktop via USB

## Download the Windows SDK##

Please 

## API Documentation ##

The primary interface to the API is through a Singleton class called **EzeAPI**. The following section describes the operations available on the EzeAPI for performing various payment related transactions exposed by the API. 


###EzeAPI###

This section documents the operations and attributes available on the EzeAPI

####Create####

        public static EzeAPI create(ServerType serverType)

The first operation exposed on the API is the Create() method. It is used to create an instance of the EzeAPI object against with the other methods are invoked. EzeAPI instance can be created either in DEMO or PROD modes by passing the corresponding ServerType enum. This method returns a singleton instance of EzeAPI object, which should be stored and used to perform all other operations.

See the [Enumerations](#Enumerations) section for more details on the Enums. 


####Login####

	    public EzeResult login(LoginMode mode, string userName, string passkey) 

This method is used to login to Ezetap server. It accepts the following parameters. 



| Input Field     | Description |
|----------------|-----------|
| LoginMode   | This is a required field with 2 values PASSWORD or APPKEY. When LoginMode is ``PASSWORD``, *userName* and *Passkey* fields are used for authenticating the individual users' credentials against the merchant account. Only valid users in the merchant account are allowed to login. When LoginMode is ``APPKEY``, the appKey registered with the merchant (*provided to the merchant along with Ezetap setup documentation*) should be passed in the *passKey* field. *userName* is not validated against the merchant, but it is stored along with the payment details for all transactoins.  |
| userName    | A valid userName in the merchant account |
| passkey    | When *LoginMode* is *PASSWORD*, individual users' password should be passed in this field. For *APPKEY*, the merchant's *appKey* should be passed in this field. |

Please refer [EzeResult](#EzeResult) section for the details of the response


####Prepare Device####

	    public EzeResult prepareDevice() 

Prepare device method should be invoked to prepare the Ezetap device for card transaction. During this method call, the EzeAPI downloads specific security keys from the acquiring bank, without which the card transactions will fail. Prepare device should be called at the following instances:

1.  Everyday when the user logs in to Ezetap API for the first time 
2.  Device wakes up from sleep or startup after a shutdown

> Note: If the EzeAPI returns an error related to *device not ready* during postPayment() transaction, please implement an option for the user to prepare the device as needed.

####Take Payment####

	    public EzeResult takePayment(PaymentType type, double amount, PaymentOptions options) 

Take payment is the primary interface for payment transactions. 

####Attach Signature####

        public EzeResult attachSignature(string txnId, ImageType imageType, ByteString imageData, int height, int width, double tipAmount)

####Set Message Handler()####

        public void setMessageHandler(EzeNotification handler)

####Logout####

        private EzeAPI logout()

Logout method is used to log out a user from the API. This method is used in a situation when multiple users are needing to use the API. While the API will be instantiated and continuously running, individual users will log in and out of the API using the login and logout methods. When using the APPKEY mode to login, there is no need to logout. Instead, destroy() method is recommended to be used to close down the API.


####Destroy()####

        public static void destroy()

This is the last operation that should be invoked on the Ezetap SDK to destroy the EzeAPI instance. This method closes the connection to Ezetap server, relinquishes the connection to the device and gracefully exists from the API.

###PaymentOptions###

	public class PaymentOptions 
	{
		public PaymentOptions setOrderId(string orderId);
		public PaymentOptions setReceiptType(string receiptType);
		public PaymentOptions setChequeNo(string chequeNo);
		public PaymentOptions setBankCode(string bankCode);
		public PaymentOptions setChequeDate(String chequeDate);
	}

The following 

###EzeResult###

EzeResult is returned whenever a response is returned to the user while invoking the EzeAPI. 

    public class EzeResult 
	{
		public PaymentResult getPaymentResult();
	    public EventName getEventName();
		public Status getStatus();
		public string getCode();
		public string getMessage();
	}


It contains the following methods:


| Attribute    | Description |
|-----------|-------------|
| paymentResult | an instance of paymentResult object that contains the details of the payment transaction |
| eventName     | Enum representing the API method invoked 
| status        | Status enum representing the status of the transaction. Valid values are SUCCESS or FAILED.  |
| code          | Ezetap error code representing the problem |
| message       | Message representing the details, in case of an error |

Please See [PaymentResult](#PaymentResult) for details on paymentResult class and [Enumerations](#Enumerations) for the different Enumerations used.

###PaymentResult###

EzeResult is returned whenever a response is returned to the user while invoking the EzeAPI. 

	public class PaymentResult 
	{
    	public string getPmtType();
    	public string getStatus();
    	public string getTxnId();
    	public double getAmount();
			public string getSettlementStatus();
    	public bool getVoidable();
    	public string getChequeNo();
    	public string getChequeDate();
    	public string getAuthCode();
    	public string getCardType();
    	public string getOrderId();
    	public string getTid();
    	public string getMid()
	}

The methods available on this class and their details are given below:


| Method    | Description |
|-----------|-------------|
| pmtType   | Payment type of the transaction (Cash, Card or Cheque)  |
| status    | Status enum representing the status of the transaction. Valid values are SUCCESS or FAILED.  |
| txnId     | Unique ID of the transaction | 
| amount    | Amount of the transaction | 
| settlementStatus| Settlement status of the txn (Pending / Settled) | 
| voidable  | Boolean indicating whether transaction is voidable | 
| chequeNo  | Cheque No passed in (only for Cheque txns) | 
| chequeDate| Cheque Date passed in (only for Cheque txns) | 
| authCode  | Auth code of the card txn | 
| cardType  | Card type of the card txn (Credit / Debit) | 
| orderId   | Order Id for the transaction, passed in by the caller during the payment transaction |
| tid	      | TID (Terminal Id) provided by the Bank for the specific terminal device of the merchant |
| mid       | MID (Merchant Id) provided by the Bank for the merchant account |


###Enumerations###

The following section documents all the enumerations that are available for use while invoking the Ezetap SDK.

####ServerType####

ServerType enum is passed while creating the EzeAPI instance. You can either pass PROD or DEMO values. This enum configures the API to either work with the production or DEMO version of the Ezetap Service.

    public enum ServerType
    {
        PROD, DEMO
    }

####LoginMode####

Users can login to the EzeAPI using either username/password or APPKEY. When  using username/password, the LoginMode is set to PASSWORD and the individual user is authenticated using the users login credentials against the merchant. When using APPKEY, authentication is performed against the APPKEY present in the merchant account.

    public enum LoginMode
    {
        PASSWORD, APPKEY
    }

####Status####

Status enum is returned as part of EzeResult that indicates if a an API call was successful or failed. 

    public enum Status 
    {
        SUCCESS, FAILURE
    }

####PaymentType####

PaymentType enum is passed as input to takePayment() API call and can accept CARD, CASH or CHEQUE as valid payment types

    public enum PaymentType
    {
        CARD, CASH, CHEQUE
    }

####ImageType####

ImageType enum is used in the attachSignature() API call for passing eSignature data in one of the acceptable image formats. 

    public enum ImageType
    {
        PNG, GIF, JPEG, BMP
    }

####EventName####

EventName enum is returned as part of the EzeResult object indicating the different API method calls invoked on EzeAPI

    public enum EventName
    {
        LOGIN, LOGOUT, EXIT, PREPARE_DEVICE, NOTIFICATION, TAKE_PAYMENT, CREATE, SET_SERVER_TYPE, SEND_RECEIPT, ATTACH_SIGNATURE, OTHER
    }
