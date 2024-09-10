# AamarPay-Integration-Documentation

## Integration Guidelines

### Overview 
aamarPay Payment Gateway enables Merchants to receive money from their customers by temporarily redirecting them to www.aamarpay.com. The gateway is connecting multiple payment terminal including card system, mobile financial system, local and International wallet . After the payment is complete, the customer is returned to the merchant's site and seconds later the Merchant receives notification about the payment along with the details of the transaction. This document is intended to be utilized by technical personne l supporting the online Merchant's website. Working knowledge of HTML forms or cURL is required. You will probably require test accounts for which you need to open accounts via contact with aamarPay.com or already provided to you. 

### API Operations 

REST AP Is are supported in two environments. Use the Sandbox environment for testing purposes, then move to the live environment for production processing. When testing, generate an order url with your test credentials to make calls to the Sandbox URIs. When you’ re set to go live, use the live credentials assigned to your new signature key to generate a live order url to be used with the live URIs .
