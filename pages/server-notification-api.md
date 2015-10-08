---
title: Notification API
description: Receiving post transaction notifications via JSON API callback
type: Server Side
layout: default 
---
<!-- Tamal and others reviewing, to review and add comments in Markdown, just add HTML style comments into the document. -->

This document describes how Ezetap customers can integrate with  the `Ezetap Notification API` to receive notifications when payment transactions are posted in the Ezetap server. 

### What is the Ezetap Notification API?

Ezetap provides a Notification API for enterprises to kick-off their internal business processes on a near real-time  basis; these notifications from the Ezetap server are generated when transactions happen or change state. 

For every transaction that hits the Ezetap payment platform, the Ezetap server has the ability to update an external system that a payment transaction has happened for the following transaction types: 

1.  Successful payment authorization
2.  Failed payment authorization
3.  Voided payment transaction
<!--4. Refunded payment transaction-->

### Why Ezetap Notifications API?
    
Customers may wish to reconcile payment information with their internal or backend systems.  Payment information that can be tied back to the original transaction reference, that too in real time provides immense value to the originating business process.  

For e.g., the API can be used for

1.     updating your systems on the status of transactions in the field (e.g. auto-reconciling settled transactions),
2.     initiating post transaction backend processes (e.g. paying out commissions to outlets),
3.     informing customers of transaction completion (e.g. additional SMS from the enterprise using their short-code, if applicable).

While conceptually this can be achieved by providing a means to query the Ezetap platform with a transaction reference; Ezetap recommends and provides a simpler interface namely the Notifications API to push the data to any external system defined by the customer.

Here are some classic examples of how Ezetap merchants have used the notification mechanism in the past, to enhance their customer engagement levels and improve internal business functions:

####Transaction Reconciliation
An e-commerce company was able to leverage Ezetap's notification API to auto-reconcile, in real time, COD payments against the order number. When the delivery agent processes a payment, be it cash or card, an order reference number is passed from the Ezetap mobile application to the Ezetap server. A notification is generated for the payment transaction, that updates the backend server of the e-commerce company with required fields to process the payment against the order.

####Insurance Policy Receipting
An insurance company was able to move to immediate policy issuance by equipping their agents with the Ezetap solution. The traditional insurance policy follows the `Cheque Collection -> Deposit -> Realization -> Issuance` cycle. 

With Ezetap's solution, they were instead able to process credit card payments at the customer's doorstep; leverage Ezetap's notification API to send payment information from the Ezetap server to the insurance company's server. Essentially `Card Payment -> Immediate Payment Reconciliation -> Immediate Policy Issuance` resulted in significantly enhanced customer experience.

<!--####Commission Calculation
//Need some specifics on this-->

####Post transaction workflow
Successful payments often trigger critical follow on business processes within an organization function. Notifications sent from the Ezetap server can be utilized to trigger specific business process workflows in the merchant's application suite.

####Customer Communication
Notification API, if enabled will post details of every transaction whether successful, failed or voided to a customer specified API end point.

###Integration steps

The steps for enabling notifications for demo and production environments are listed here. The steps are described in detail in subsequent sections.

####Demo

| Step       | Details |
|------------|----------------|
| Setup merchant | Contact Ezetap to setup your merchant information in the demo environment. You will need name, contact, address,category and mobile number |
| Implement web service | Expose an API endpoint to accept a JSON structure. Refer to Ezetap Notification API specifications below <!--provide link--> |
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

<!-- Other production steps?-->

###API Specification

<!--this section needs work-->
The API end point needs to conform to the following specification. 

The following headers are sent in the HTTP request.
	
	URL: Any Customer URL (REST API)
	HTTP Method: POST
	Content-Type: application/json
	Request Body: JSON encoded key-value pairs are sent in the request body.

Customer should expose a `HTTP/POST` end point accepting `JSON message body` 
<!-- Update to use NGROK instead -->

> Note: Once Customer builds a Restful service end point accepting 'HTTP/POST' request `Callback URL`, they should work with Ezetap support team to enable the Notification API to the `Callback URL` exposed at the customer end.

####Processing the notification messages
The following considerations must be handled at the customer end when interpreting notifications from Ezetap:

1. Ezetap sends a POST message on the customer's API end point and waits for a HTTP/Success response (Status 200). In case a HTTP Success is not received (due to various reasons, including network connectivity, timeout etc.), Ezetap will retry upto 3 times (at an interval of 10 minutes each). If no HTTP/Success response is received after the 3 attempts, the notification is marked as FAILED and no additional attempts will be made. 

2. There may be scenarios when the customer has received the notification and processed them, but failed in responding to Ezetap. In such cases, Ezetap will keep retrying. In such cases, customer's application should be able to handle (and ignore) duplicate notifications for the same transaction.

3. Over time, the Notification API may be upgraded with additional parameters. These additional parameters will be optional and will not impact existing customers. But the customer's API end point should be able to handle (and ignore) these additional optional parameters. This is to ensure merchant's application doesn't break when new attributes are introduced in the notification API.

#### JSON Sample structure###

The JSON posted will have this structure, with sample data included.

    {
	"errorCode": "EZETAP_1000007",
    "errorMessage": "Invalid Amount. Please verify amount and try again.",
    "amount": 513,
    "amountAdditional": 0,
    "amountOriginal": 513,
    "amountCashBack": 0,
    "authCode": "ABCDEF",
    "batchNumber": "5",
    "cardLastFourDigit": "3302",
    "currencyCode": "INR",
    "customerName": "Tamal Das",
    "customerMobile": "9845102105",
    "customerEmail": "tamal@ezetap.com",
    "customerReceiptUrl": "http://d.eze.cc/r/x012345",
    "deviceSerial": "210011039406",
    "externalRefNumber": "AFN00005",
    "externalRefNumber2": "HT_FRESH_2",
    "externalRefNumber3": "NEW",
    "formattedPan": "5546-37XX-XXXX-3302",
    "txnId": "150902092354668E010018959",
    "merchantName": "HT Media Limited",
    "mid": "801111111100001",
    "orgCode": "HT_MEDIA_LIMITED",
    "payerName": "TAMAL  DAS",
    "paymentCardBin": "554637",
    "paymentCardBrand": "MASTER_CARD",
    "paymentCardType": "CREDIT",
    "paymentMode": "CARD",
    "rrNumber": "0123456789",
    "settlementStatus": "FAILED",
    "status": "FAILED",
    "tid": "11100001",
    "userMobile": "8011111111",
    "txnType": "CHARGE",
    "chargeSlipDate": "2015-09-02T14:53:55+0530",
    "readableChargeSlipDate": "02/09/2015 14:53:55",
    "issuerCode": "CITI",
    "receiptUrl": "http://d.eze.cc/r/x012345",
    "signReqd": false,
    "acquirerCode": "CITI",
    "pgErrorCode": "DUMMY_513",
    "pgErrorMessage": "INVALID AMOUNT",
    "orderNumber": "AFN00005",
    "reverseReferenceNumber": "0123456789"
		}


####Field Descriptions###
JSON structure for different events and processes are documented below. Some fields are optional, for e.g. Cheque payment related fields (bank details etc) will be populated only for cheque transactions. Card related fields will be populated only for Card payment.
                   
| Field | Data type | Description |Success| Failure| Void|
|-------|---------|-------------|-----|-----|-----|
| amount | double | total amount  | | | |
| amountAdditional | double | additional amount. for e.g. tip  | | | |
| amountOriginal | double | original amount  | | | |
| amountCashBack | double | cash back amount  | | | |
| authCode | string | authorization code given by the card issuing bank for an authorized transaction | | | |
| batchNumber | string | batch no. of the transaction provided by the card issuing bank. Shows up on customer’s chargeslip.  | | | |
| currencyCode | string | currency code of the merchant  | | | |
| customerName | string | if card transaction: this is cardholder’s name. Otherwise this is empty, or populated with the manually entered input | | | |
| customerReceiptUrl | string | customer receipt url  | | | |
| deviceSerial | string | serial no. of the device used for card payment | | | |
| externalRefNumber | string | reference no. If not input during the transaction, this is auto generated.  | | | |
| formattedPan | string | payment card’s pan (primary account number) with first 6 and last 4 digits  | | | |
| invoiceNumber | string | invoice no. of the transaction - same as pgInvoiceNumber  | | | |
| mid | string | MID (merchant ID) used for the transaction  | | | |
| payerName | string | payer's name  | | | |
| paymentCardBrand | string |  card brand. Valid values: VISA, MASTER_CARD, DISCOVER, DINERS, AMEXJCB, UNKNOWN | | | |
| paymentCardType | string | payment card's type. Valid values: CREDIT, DEBIT, UNKNOWN  | | | |
| paymentMode | string | payment mode. Valid values: CARD, CASH, CHEQUE  | | | |
| pgInvoiceNumber | string | invoice no. of the transaction, as provided by payment gateway. This shows up on the customer’s chargeslip <!-- see chargeslip sample below this table-->  | | | |
| postingDate | long | transactions date, time in milliseconds from epoch  | | | |
| rrNumber | string | rrn (reference retrieval number) of the transaction provided by payment gateway. This shows up on the customer’s chargeslip  | | | |
| settlementStatus | string | settlement status of the transaction. Valid values: <ul><li>PENDING - transaction authorized, but not settled with payment gateway yet</li><li>SETTLED - transaction successfully settled with payment gateway</li><li>FAILED - transaction failed, hence not settled</li><li>POSTED - transaction sent for settlement, waiting for response from payment gateway</li></ul>| | | | 
| status | string | Transaction status. Valid values: <ul><li>AUTHORIZED - transaction authorized by issuing bank</li> <li>REFUND_PENDING - refund is initiated, but not posted to acquiring bank yet</li><li>AUTHORIZED_REFUNDED - original authorized transaction that has been successfully refunded</li><li>REFUNDED - refund successful</li><li>VOIDED - transaction has been successfully voided</li><li>FAILED - transaction failed</li></ul> | | | |
| tid | string | TID (Terminal ID) used for the transaction  | | | | 
| txnId | string | transaction ID  | | | |
| txnType | string | transaction type. Valid values <ul><li>CHARGE - transaction type for card, cash or cheque transactions</li><li>REFUND - transaction type for refund transaction</li><li>CASH_BACK - transaction type for Sale + Cash @ POS transaction</li><li>CASH_OUT - transaction type for Cash @ POS (no Sale) transaction</li></ul> | | | |
| userAgreement | string | Agreement on which card holder needs to sign if required.  | | | |
| username | string | username of the user that did the transaction  | | | |
| externalRefNumber | string | customer reference number 1  | | | |
| externalRefNumber2 | string | customer reference number 2  | | | |
| externalRefNumber3 | string | customer reference number 3  | | | |
| errorCode | string | Ezetap errorCode in case the transaction failed.  | | | |
| errorMessage | string | Error message shown to the user in case the transaction failed.  | | | |



