---
title: Merchant Portal
description: Understanding Merchant Configuration Settings
type: Server Side
layout: default
---

The Merchant portal is a one-stop portal to view all merchant related setups including user information, devices or assets tied to your organization and transaction summary and status.

The access to the portal is role based and some of the options may only be available to the administrator of your portal.

#Login

Login to the [Merchant portal](http://d.eze.cc/portal/login/) using your phone number and password. If you do not have access to the portal via your login, please contact Ezetap support.
![]()

#Users
Users associated with your merchant profile can be viewed only by the administrator associated with your merchant. A user typically has one or more roles associated, which grant certain privileges in the system

Agent: Can transact using the PoS application.Cannot void transactions or access the portal.

Agent (with Void): Can transact and also void transactions created by him or her.

Agent(With Portal): Can access the Merchant portal and review his or her transactions.

Admin: Can access the portal, review transactions across all users, review user information, void transactions across all users, view devices associated with his organization and view application keys generated for his merchant profile.

Refund: Allows a user to process refund transactions for previously settled transactions.

#Review Transactions
If you are a merchant administrator, the transactions screens lets you filter transactions for your organization by date range, device serial number and specific users. You can drill down on specific transaction, review transaction details, and void them if required.

If you are an agent, you will be able to review only those transactions associated with your Ezetap device.

#App Keys
This screen allows an administrator to review application keys that have been generated on behalf of your merchant profile. The application key gives a merchant specific handle for authentication using any custom applications built for your organization, when calling the SDK APIs.

#Assets
The assets screen lets an administrator review the status of all Ezetap devices associated with his or her organization. The administrator can activate or deactivate devices, review when a transaction was last performed on a particular device and the user associated with the device.
