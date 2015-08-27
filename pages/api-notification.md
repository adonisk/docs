---
title: Notifications API
description: Receiving post transaction notifications via JSON API callback
type: Server API
layout: default 
---

##Overview##

This document provides information about how Ezetap customers can integrate with Ezetap’s data posting APIs. Currently, Ezetap has the ability to post to external applications for Payment transactions. Ezetap can post to an external system whenever a payment transaction happens. The post happens even when a transaction fails due to some reason. Merchants need to provide a URL to which Ezetap can post.

> Ezetap posts the notification to external systems and waits for a HTTP Success response (Status 200). In case a HTTP Success is not received (due to network connectivity failure, timeout etc.), Ezetap will attempt to notify the external system for a maximum of 3 times (at an interval of 10 minutes each). If no HTTP Success response is received after 3 attempts, the notification is marked as FAILED (no additional attempts will be tried). 



There may be scenarios when merchant has successfully received the data but Ezetap couldn't receive a response. In such cases, Ezetap will keep retrying. Merchant application should be able to handle multiple posts for the same transaction.

###Configuration###

Merchant has to provide Ezetap with a URL where data can be posted. Also, Ezetap needs to whitelist IP address where merchant runs the application.

The following headers are sent in the HTTP request.
	
	URL: Registered Merchant URL
	HTTP Method: POST
	Content-Type: application/json
	Request Body: JSON encoded key-value pairs are sent in the request body.

Merchant needs to ignore any undocumented attributes that may come with the request body. Merchants application should not expect undocumented fields to be present in future. It will ensure merchant's application doesn't break when Ezetap introduces new fields or removes undocumented fields.

## API Documentation ##

JSON structure for different events and processes are documented below.

> Some fields may not be available all the time. For e.g. In case of CASH transactions, the body won't have card related fields like  formatted card no. or authorization code from payment gateway.


###Callback  JSON###

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
		}


###Field Descriptions###
                   
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
| errorCode | string | Ezetap errorCode in case the transaction failed. |
| errorMessage | string | Error message shown to the user in case the transaction failed. |



