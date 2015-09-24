---
layout: default
title: Ezetap Error Codes
description: Error codes and their meaningsr
type: Help
---

The message against each error code will describe the event and action to be taken.

###Ezetap Error Codes

Below the list of error codes that typically user can come across while doing a transaction/initialize device.

| Error Code         | Reasoning         |
| ------------------ | ----------------- |
|   EZETAP_0000000   | An error occurred while processing the request on Ezetap. Please try again.  |
|   EZETAP_0000001	 | An error occurred while connecting to Ezetap payment platform. Please try again. |
|   EZETAP_0000002	 | API version is invalid. SESSION_EXPIRED	Your session has expired. Please login again. |
|   EZETAP_0000003	 | Your session has expired. Please login again.       |
|   EZETAP_0000004	 | User cannot perform this operation.                 |
|EZETAP_0000005|	This is an unsupported operation.|
|EZETAP_0000006|	Invalid email address detected. Please enter a valid email address.|
|EZETAP_0000007|	Name must be more than 3 characters and can containing letters, hyphen, period and space.|
|EZETAP_0000008|	Username must be more than 3 characters containing letters and numbers. Recommended to use your mobile number.|
|EZETAP_0000009|	Password is too short.|
|EZETAP_0000010|	Mobile number should have less than 13 digits. You entered {0}.|
|EZETAP_0000011|	App not found with Id: {0} and version code: {1}|
|EZETAP_0000012|	Bad swipe detected. Please make sure that the Ezetap Device is connected properly and try again.|
|EZETAP_0000013|	Ezetap Device cannot be used because it is already registered to another merchant. Please contact Ezetap Customer Support.|
|EZETAP_0000014|	Ezetap Device has been deactivated. Please contact Ezetap Customer Support.|
|EZETAP_0000015|	Unexpected Serial Length: {0}. Please try again.|
|EZETAP_0000016|	Ezetap Device is already registered with a different serial.|
|EZETAP_0000017|	Ezetap Device Registration or Activation Failed. Please try again.|
|EZETAP_0000018|	Ezetap Device could not be identified. Please make sure that the Ezetap Device is connected properly and try again.|
|EZETAP_0000019|	You cannot use this Ezetap Device.|
|EZETAP_0000020|	Another Ezetap Device exists with the Serial No: {0}.|
|EZETAP_0000021|	Cannot assign a Terminal to Ezetap Device.|
|EZETAP_0000022|	A device couldn't not be determined. Either session expired or device doesn't exist. Please register the Ezetap Device and enter Serial No. again.|
|EZETAP_0000023|	Invalid Licence Label: {0}|
|EZETAP_0000024|	Signature already captured for {0}|
|EZETAP_0000025|	Invalid Transaction ID: {0}|
|EZETAP_0000026|	Transaction not found {0}|
|EZETAP_0000027|	Transaction cannot be voided in its current status.|
|EZETAP_0000028|	Did not find transactionId: {0} for automatic void.|
|EZETAP_0000029|	Transaction is not authorized.
|EZETAP_0000030|	Processing failed. A Terminal could not be identified for {0} card. Please try a different card.|
|EZETAP_0000031|	Processing failed. Please try again.|
|EZETAP_0000032|	Processing Failed. Unable to get response from Ezetap payment platform. Please try again.|
|EZETAP_0000033|	You have already made a similar payment for the same Ref# {0} for the same amount {1}. Please check the status of the payment(s) made before you proceed.|
|EZETAP_0000034|	Processing failed. Please try again.|
|EZETAP_0000035|	Refund already processed.|
|EZETAP_0000036|	Tip already processed.|
|EZETAP_0000037|	Reference number has unsupported characters {0}. Please try again.|
|EZETAP_0000038|	Amount more than original.|
|EZETAP_0000039|	Amount is invalid.|
|EZETAP_0000040|	Card swiped in pre auth and confirm/release order is not the same.|
|EZETAP_0000041|	Processing failed. Please try again.|
|EZETAP_0000042|	Card requires PIN and is not supported currently. Please use any Visa or MasterCard? that does not require a PIN.|
|EZETAP_0000043|	Automatic void failed.|
|EZETAP_0000044|	Please enter card\'s last 4 digits and try again.|
|EZETAP_0000045|	The last 4 digits entered by the user don't match card\'s last 4 digits.|
|EZETAP_0000046|	Tip cannot be processed for this Transaction.|
|EZETAP_0000047|	Tip amount is greater than allowed.|
|EZETAP_0000048|	Tip is not enabled for this merchant.|
|EZETAP_0000049|Invalid Tip Amount.|
|EZETAP_0000050|	Transaction amount is greater than the allowed limit.|
|EZETAP_0000051|	Limit for number of transactions allowed per day has been reached.|
|EZETAP_0000052|	Limit for total transaction amount for the day has been reached.|
|EZETAP_0000053|	No process data found|
|EZETAP_0000054|	The specified process code does not exist for the merchant. Please contact Ezetap Support.|
|EZETAP_0000055|	Specified data could not be deleted. Please contact support.|
|EZETAP_0000056|	Terminals not configured for merchant.|
|EZETAP_0000057|	An active Terminal could not be found. Please try again.|
|EZETAP_0000058|	Terminal could not be found for ID: {0}|
|EZETAP_0000059|	Payment Failed. All terminals are busy. Please try again after some time.|
|EZETAP_0000060|	Terminal settlement failed for {0}|
|EZETAP_0000061|	No transaction records found.|
|EZETAP_0000062|	Transaction already signed {0}|
|EZETAP_0000063|	Transaction update failed.|
|EZETAP_0000063|	Change password failed: {0}|
|EZETAP_0000064|	Passwords entered should match.|
|EZETAP_0000065|	Password has already been used before.|
|EZETAP_0000066|	Password too short|
|EZETAP_0000067|	Password has repeating characters|
|EZETAP_0000068|	Password has sequences like 123|
|EZETAP_0000069|	Password has invalid characters|
|EZETAP_0000070|	Minimum alphanumeric and numeric characters not found.|
|EZETAP_0000071|	Password has been used before.|
|EZETAP_0000072|	Password not changed. Please try again.|
|EZETAP_0000073|	Invalid credentials. Verify your credentials, login again, or contact your supervisor.|
|EZETAP_0000074|	Switch Exception thrown. Settlement Failed.|
|EZETAP_0000075|	Message cannot be saved without a code.|
|EZETAP_0000076|	Payment Succeeded. Data Update Failed.|
|EZETAP_0000077|	Receipt could not be sent.|
|EZETAP_0000078|	Message not found with code {0}|
|EZETAP_0000079|	Ezetap payment platform received an unauthenticated request.|
|EZETAP_0000080|	Terminal was busy processing last transaction. Please try again.|
|EZETAP_0000081|	Payment Failed. We are still processing last request from the Ezetap Device. Payment gateways can take up to 2 minutes to respond. Please try again later.|
|EZETAP_0000082|	Payment Failed. Please try again.|
|EZETAP_0000083|	The transaction is being updated by another request. Please try again after some time.|
|EZETAP_0000084|	You have attempted a similar payment for the same amount {0} using the same card within {1}. Please check the status of the payment(s) made before you proceed. To make another payment with the same card, try after {1}.|
|EZETAP_0000085|	You can not create messages. Please contact system administrator.|
|EZETAP_0000086|	This message can not be changed or overridden.|
|EZETAP_0000087|	Card Declined. Merchant does not support cards starting with {0}. Please try a different Debit card.|
|EZETAP_0000088|	Ezetap Device has not been registered. Please register the device.|
|EZETAP_0000089|	Unable to get information from card. Please make sure that the Ezetap Device is connected properly and try again.|
|EZETAP_0000090|	Signature is not required for a failed transaction.|
|EZETAP_0000091	|Unsupported payment gateway for this request.|
|EZETAP_0000092|	Terminal Settlement Failed.|
|EZETAP_0000093|	Terminal not configured properly. Please contact Ezetap Support.|
|EZETAP_0000094|	No such catalog was found, please check the catalog code.|
|EZETAP_0000095|	Error parsing JSON request.|
|EZETAP_0000096|	Catalog with this code already exists.|
|EZETAP_0000097|	Amount has to be in INR.|
|EZETAP_0000098|	{0} Error : External server responded with failure message - {1}|
|EZETAP_0000099|	Error in configuration of Ezetap adapter. Please contact Ezetap support|
|EZETAP_0000100|	Invalid response from merchant server. Please contact Ezetap support|
|EZETAP_0000101|	Integration Error|
|EZETAP_0000102|	Catalog is not enabled for the merchant|
|EZETAP_0000103|	{0} Error : Catalog could not be retrieved from the remote server|
|EZETAP_0000104|	{0} Error : Unable to establish connection with server|
|EZETAP_0000105|	Processing Failed. Refund is not allowed for EMI transactions.|
|EZETAP_0000106|	EMI Term missing from setup.|
|EZETAP_0000107|	Issuer code is invalid or missing from setup.|
|EZETAP_0000108|	Merchant acquisition not setup.|
|EZETAP_0000109|	Acquirer code is invalid or missing from setup.|
|EZETAP_0000110|	Invalid EMI selected. Please try a valid EMI option.|
|EZETAP_0000111|	Processing Failed. Amount entered is less than minimum required by the EMI option selected.|
|EZETAP_0000112|	Processing Failed. We could not find a terminal for the EMI selected. Please contact Ezetap Support.|
|EZETAP_0000113|	Processing Failed. Card issuing bank doesn't support EMI payments with this card. Please choose a different option to pay or make a full payment.|
|EZETAP_0000114|	Processing Failed. EMI is not supported by the merchant.|
|EZETAP_0000115|	Processing Failed. The selected EMI option is inactive.|
|EZETAP_0000116|	File Upload Failed. Please make sure the size of the file does not exceed 1 MB.|
|EZETAP_0000117|	You have a pending Pre auth in the system. Please confirm that pre auth first and then try again.|
|EZETAP_0000118|	Amex card is not supported for payment, please use VISA/Master Card.|
|EZETAP_0000119|	Invalid Value for maximum refund allowed: {0}. Please enter a value greater than -100.|
|EZETAP_0000120|	Processing Failed. Refund is not allowed for the merchant.|
|EZETAP_0000121|	Processing Failed. Amount can not be more than refundable amount. Original Amount: {0} Amount To Refund: {1} Refundable Amount: {2}|
|EZETAP_0000122|	Processing Failed. Transaction can not be refunded in its current status.|
|EZETAP_0000123|	Operation Failed. Multiple Devices found with the serial selected.|
|EZETAP_0000124|	Operation Failed. Labels need to be configured. Please contact Ezetap Support.|
|EZETAP_0000125|	Operation Failed. A terminal matching the given selection could not be found. Please contact Ezetap Support.|
|EZETAP_0000126|	Reversal Failed. Payment reversal is pending.|
|EZETAP_0000127|	Process Data not saved. ref missing for item no. {0}|
|EZETAP_0000128|	Process Data save failed for item no. {0}. Items before this entry could have been saved. Reason: {1}|
|EZETAP_0000129|	Please specify process code. If you are not aware of it, please contact Ezetap Support.|
|EZETAP_0000130|	Operation Failed. New Keys are required by the device. Please pair the device and try again.|
|EZETAP_0000131|	Processing Failed. Please pair the device and try again.|
|EZETAP_0000132|	Processing Failed. Random number not found. Please try again.|
|EZETAP_0000133|	Pin is required for this transaction.|
|EZETAP_0000134|	Pairing Failed. Please try again.|
|EZETAP_0000135|	Pairing failed while trying to exchange keys. Please try again.|
|EZETAP_0000136|	Pairing Failed. Terminals used by Device need to be settled. Please contact Ezetap Support.|
|EZETAP_0000137|	Unable to download Ezetap Service Application. Please contact Ezetap Support.|
|EZETAP_0000138|	Chip Card declined transaction.|
|EZETAP_0000139|	Failed! You need to upgrade to the new Ezetap Chip & PIN enabled device. Please contact Ezetap Support 080-49114999.|
|EZETAP_0000140|	Incorrect old password.|
|EZETAP_0000141|	Failed to find a terminal for device used. Please contact Ezetap Support.|
|EZETAP_0000142|	Device Serial has already been registered with a different Device ID. Please contact Ezetap Support.|
|EZETAP_0000143|	Cache Refresh Failed.|
|EZETAP_0000144|	Txn can not be reversed in its current status.|
|EZETAP_0000145|	Txn can not be confirmed in its current status.|
|EZETAP_0000146|	Merchant Acquisition record not found.|
|EZETAP_0000147|	Merchant Acquisition already exists with this combination.|
|EZETAP_0000148|	Invalid Org Code.|
|EZETAP_0000149|	Ezetap Servers are initializing. Please try after some time.|
|EZETAP_0000150|	Processing Failed. Could not connect to Ezetap Payment Platform. Please try after some time.|
|EZETAP_0000151|	Processing Failed. Invalid terminal passed. Please contact Ezetap Support.|
|EZETAP_0000152|	Processing Failed. Terminal selected not available for merchant.|
|EZETAP_0000153|	Processing Failed. Amount entered is less than minimum required by the terminal.|
|EZETAP_0000154|	Processing Failed. Terminal is inactive. Please contact Ezetap Support.|
|EZETAP_0000155|	Processing Failed. Both EMI and Terminal options can't be selected. Please select only one.|
|EZETAP_0000156|	Card Not Supported.|
|EZETAP_0000157|	Void not allowed For this transaction.|
|EZETAP_0000158|	Cash Back amount has to be greater than 0.|
|EZETAP_0000159|	Process Data information is missing. Please contact Ezetap Support.|
|EZETAP_0000160|	Txn Processing Failed.|
|EZETAP_0000161|	Recurring Process Data not found. Please contact Ezetap Support.|
|EZETAP_0000162|	Transaction amount is less than the allowed limit.|
|EZETAP_0000163|	Cash Back amount greater than configured.|
|EZETAP_0000164|	Processing Failed. Amount entered is more than maximum allowed for the terminal.|
|EZETAP_0000165|	Change not allowed as some terminals are not settled. Please settle terminals before making changes.
|EZETAP_0000166|	Cash Back not allowed.|
|EZETAP_0000167|	This transaction is not allowed without PIN. Please enter PIN and try again|
|EZETAP_0000168|	Cash Payment is not enabled for the merchant. Please contact Ezetap Support.|
|EZETAP_0000169|	Cheque Payment is not enabled for the merchant. Please contact Ezetap Support.|
|EZETAP_0000170|	Bank Code, Cheque No. and Cheque Date are mandatory for cheque payment.|
|EZETAP_0000171|	Invalid Date format for Cheque Date. Please pass cheque date in yyyy-MM-dd format.|
|EZETAP_0000172|	Invalid File. Please check whether file format is different from what is expected.|
|EZETAP_0000173|	Invalid no. of headers. Please make sure no. of headers are more than {0} and less than {1}.|
|EZETAP_0000174|	No. of headers and descriptions don't match.
|EZETAP_0000175|	Duplicate headers found: {0}|
|EZETAP_0000176|	Invalid Start Date: {0}|
|EZETAP_0000177|	Invalid End Date: {0}|
|EZETAP_0000178|	End date occurs before start date.|
|EZETAP_0000179|Invalid Frequency: {0}|
|EZETAP_0000180|	Invalid Frequency Interval: {0}|
|EZETAP_0000181|	Data Received from device serial {0}. Txn will fail.|
|EZETAP_0000182|	NO DATA RECEIVED FROM DEVICE SERIAL {0}. Txn will fail.|



###PGW Error Codes

Below the list of error codes that typically Payment Gateway will throw out while processing the payment request.


| Error Code         | Reasoning         |
| ------------------ | ----------------- |
|EZETAP_1000000|	Transaction Approved.|
|EZETAP_1000001|	Payment Failed. Please try again. If the problem persists, please try another card or contact card issuer.|
|EZETAP_1000002|	Payment Failed. Please try again. If the problem persists, please contact Ezetap Support.|
|EZETAP_1000003|	Card Declined. Please try again. If the problem persists, please try another card or contact card issuer.|
|EZETAP_1000004|	Payment Failed. Please verify ID and signature of the card holder.|
|EZETAP_1000005|	Payment Failed. Please try again.|
|EZETAP_1000006|	Partially Approved.|
|EZETAP_1000007|	Invalid Amount. Please verify amount and try again.|
|EZETAP_1000008|	Expired Card / Invalid Expiration Date. Please use a valid card.|
|EZETAP_1000009|	Card Declined. This card can not be used due to security reasons. Please use another card.|
|EZETAP_1000010|	Exceeded PIN attempts. Please try another card.|
|EZETAP_1000011|	Invalid Checking Account. Please try another card or contact card issuer.|
|EZETAP_1000012|	Invalid Savings Account. Please try another card or contact card issuer.|
|EZETAP_1000013|	Invalid PIN. Please try again.|
|EZETAP_1000014|	Amount Exceeds Card Limit. Please use a card with higher limit.|
|EZETAP_1000015|	Card Use Limit Exceeded. Please use another card.|
|EZETAP_1000016|	Settlement Failed. Batch already open.|
|EZETAP_1000017|	Settlement Failed. Bad batch number.|
|EZETAP_1000018|	Key Exchange Failure.|
|EZETAP_1000019|	Invalid Currency. Please use INR.|
|EZETAP_1000020|	Payment Failed. Card does not have enough points.|
|EZETAP_1000021|	Payment Failed. Please try after some time.|
|EZETAP_1000022|	Payment Failed. Please try after 5 minutes.|
|EZETAP_1000023|	Settlement Failed. Total does not match.|
|EZETAP_1000024|	Settlement Failed. Transaction not found.|
|EZETAP_1000025|	Settlement Failed. Batch not found.|
|EZETAP_1000026|	Approved. Ask customer to call card issuer.|
|EZETAP_1000027|	Transaction Failed. Terminal not configured. Please contact Ezetap Support.|
|EZETAP_1000028|	Invalid Merchant Setup. Please contact Ezetap Support.|
|EZETAP_1000029|	Invalid Credit Account. Please contact card issuer.|
|EZETAP_1000030|	Invalid Account. Please contact card issuer.|
|EZETAP_1000031|	Insufficient Funds. Please use another card.|
|EZETAP_1000032|	Cash Limit Exceeded. Please use another card.|
|EZETAP_1000033|	International Card Not Accepted. Please try another card. |


