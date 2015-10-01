---
title: Notification API
description: Receiving post transaction notifications via JSON API callback
type: Server Side
layout: default 
---
<!-- Tamal and others reviewing, to review and add comments in Markdown, just add HTML style comments into the document. -->


This document describes how Ezetap customers can integrate with  the `Ezetap Notification API` to receive notifications when payment transactions are posted in the Ezetap server. 

### What is the Ezetap Notification API?
For every transaction that hits the Ezetap Payment platform, the Ezetap server has the ability to update an external system that a payment transaction has happened.

### Why Ezetap Notifications API?
Customers may wish to reconcile payment information with their internal or backend systems.  Payment information that can be tied back to the original transaction reference, that too in real time provides immense value to the originating business process.  

While conceptually this can be achieved by providing a means to query the Ezetap platform with a transaction reference; Ezetap recommends and provides a simpler interface namely the Notifications API to push the data to any external system defined by the customer.

### Notification Categories
Ezetap provides notifications for the following transaction types: 
Authorization
Void


### Customer Use Cases for the Notifications API

####Transaction Reconciliation
An e-commerce company was able to leverage Ezetap's notification API to auto-reconcile, in real time, COD payments against the order number. When the delivery agent processes a payment, be it cash or card, an order reference number is passed from the Ezetap mobile application to the Ezetap server. A notification is generated for the payment transaction, that updates the backend server of the e-commerce company with required fields to process the payment against the order.

####Insurance Policy Receipting
An insurance company was able to move to immediate policy issuance by equipping their agents with the Ezetap solution. The traditional insurance policy follows the `Cheque Collection -> Deposit -> Realization -> Issuance` cycle. 

With Ezetap's solution, they were instead able to process credit card payments at the customer's doorstep; leverage Ezetap's notification API to send payment information from the Ezetap server to the insurance company's server. Essentially `Card Payment -> Immediate Payment Reconciliation -> Immediate Policy Issuance` resulted in significantly enhanced customer experience.

####Commission Calculation
//Need some specifics on this

####Post transaction workflow
Successful payments often trigger critical follow on business processes within an organization function. Notifications sent from the Ezetap server can be utilized to trigger specific business process workflows in the merchant's application suite.

####Customer Communication
Notification API, if enabled will post details of every transaction whether successful, failed or voided to a customer specified API end point.

###Integrating with the Ezetap Notifications API

The steps for enabling notifications for demo and production environments are listed here. The steps are described in detail in subsequent sections.

####Demo

| Step       | Details |
|------------|----------------|
| Setup merchant | Contact Ezetap to setup your merchant information in the demo environment. You will need name, contact, address,category and mobile number |
| Implement web service | Expose an API endpoint to accept a JSON structure per Ezetap Notification API specifications |
| Enable notifications | Contact Ezetap to configure your merchant profile to accept notifications from Ezetap |
| Test the integration |  Perform Payment transactions and check JSON response structures  |
| Build notification processing logic | Based on the JSON response for various notification scenarios, build business logic inside your web service |	
| Perform UAT | Complete end to end UAT for the business scenarios applicable |
| Rollover to production | Request cutover to Ezetap production |		
| test using lists within table | <ul><li>item1</li><li>item2</li></ul> |

<!-- Either use lists or add details here to articulate details of each step above -->

####Production

| Step       | Details |
|------------|----------------|
| Setup merchant | Contact Ezetap to setup your merchant information in the **Production** environment |
| Enable notifications | Contact Ezetap to configure your merchant profile to accept notifications from Ezetap. IP whitelisting required. |

###API Specification

Customer should expose a `HTTP/POST` end point accepting `JSON message body` 
<!-- Update to use NGROK instead -->

> Note: Once Customer builds a Restful service end point accepting 'HTTP/POST' request `Callback URL`, they should work with Ezetap support team to enable the Notification API to the `Callback URL` exposed at the customer end.

Ezetap sends a POST message on the customer's API end point and waits for a HTTP/Success response (Status 200). In case a HTTP Success is not received (`due to various reasons, including network connectivity, timeout etc.`), Ezetap will retry upto 3 times (at an interval of 10 minutes each). If no HTTP/Success response is received after the 3 attempts, the notification is marked as FAILED and no additional attempts will be made. 

	There may be scenarios when the customer has received the notification and processed them, but failed in responding to Ezetap. In such cases, Ezetap will keep retrying. In such cases, customer's application should be able to handle (and ignore) duplicate notifications for the same transaction.

> NOTE: Over time, the Notification API may be upgraded with additional parameters. These additional parameters will be optional and will not impact existing customers. But the customer's API end point should be able to handle (and ignore) these additional optional parameters. This is to ensure merchant's application doesn't break when new attributes are introduced in the notification API.

#### API Documentation ####

The API end point needs to conform to the following specification. 

The following headers are sent in the HTTP request.
	
	URL: Any Customer URL (REST API)
	HTTP Method: POST
	Content-Type: application/json
	Request Body: JSON encoded key-value pairs are sent in the request body.

JSON structure for different events and processes are documented below. Some fields are optional, for e.g. Cheque payment related fields (bank details etc) will be populated only for cheque transactions. Card related fields will be populated only for Card payment.


#### JSON Specification###

JSON that will be posted will have this structure.

    {
		"amount": 2,
    	"amountAdditional": 0,
		"amountCashBack": 0,
    	"amountOriginal": 2,
    	"authCode": "D40533",
    	"batchNumber": "1",
    	"currencyCode": "INR",
    	"customerName": "John Doe",
    	"customerReceiptUrl": "http://192.168.1.106/portal/r/o/MnicpI6h",
    	"deviceSerial": "010001009702",
    	"externalRefNumber": "order-01",
    	"formattedPan": "4386-28XX-XXXX-4009",
    	"invoiceNumber": "2",
    	"mid": "FG-DUMMY-MID",
    	"payerName": "John Doe",
    	"paymentCardBrand": "VISA",
    	"paymentCardType": "CREDIT",
    	"paymentMode": "CARD",
    	"pgInvoiceNumber": "2",
    	"postingDate": 1423861938000,
    	"rrNumber": "RR40533",
    	"settlementStatus": "PENDING",
    	"stan": "2",
    	"status": "AUTHORIZED",
    	"tid": "TERM-0",
    	"txnId": "150214024218252E010000028",
    	"txnType": "CHARGE",
    	"userAgreement": "I agree to pay as per ... and receive chargeslip ...",
    	"username": "9111111111"
        "externalRefNumber": "customer specific reference 1"
        "externalRefNumber2": "customer specific reference 2"
        "externalRefNumber3": "customer specific reference 3"
		}


####Field Descriptions###
                   
| Field | Data type | Description |
|-------|---------|-------------|
| amount | double | total amount  |
| amountAdditional | double | additional amount. for e.g. tip |
| amountOriginal | double | original amount |
| amountCashBack | double | cash back amount |
| authCode | string | authorization code given by the card issuing bank |
| batchNumber | string | batch no. of the transaction |
| currencyCode | string | currency code of the merchant |
| customerName | string | customer's name |
| customerReceiptUrl | string | customer receipt url |
| deviceSerial | string | serial no. of the device used for card payment |
| externalRefNumber | string | reference no. it is generated if not provided |
| formattedPan | string | payment card's pan with first 6 and last 4 digits |
| invoiceNumber | string | invoice no. of the transaction |
| mid | string | MID used for the transaction |
| payerName | string | payer's name |
| paymentCardBrand | string |  card brand. Valid values: VISA, MASTER_CARD, DISCOVER, DINERS, AMEXJCB, UNKNOWN |
| paymentCardType | string | payment card's type CREDIT, DEBIT, UNKNOWN |
| paymentMode | string | payment mode. valid values: CARD, CASH, CHEQUE |
| pgInvoiceNumber | string | invoice no. of the transaction, as provided by payment gateway |
| postingDate | long | transactions date, time in milliseconds from epoch |
| rrNumber | string | rrn of the transaction provided by payment gateway |
| settlementStatus | string | settlement status of the transaction | 
| status | string | Transaction status. valid values: AUTHORIZED, REFUND_PENDING, AUTHORIZED_REFUNDED, REFUNDED, VOIDED, VOID_PENDING, FAILED |
| tid | string | TID used for the transaction | 
| txnId | string | transaction ID |
| txnType | string | transaction type. valid values CHARGE, REFUND, CASH_BACK, CASH_OUT |
| userAgreement | string | Agreement on which card holder needs to sign if required. |
| username | string | username of the user that did the transaction |
| externalRefNumber | string | customer reference number 1 |
| externalRefNumber2 | string | customer reference number 2 |
| externalRefNumber3 | string | customer reference number 3 |
| errorCode | string | Ezetap errorCode in case the transaction failed. |
| errorMessage | string | Error message shown to the user in case the transaction failed. |



