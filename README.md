# AamarPay-Integration-Documentation

## Integration Guidelines

### Overview 
aamarPay Payment Gateway enables Merchants to receive money from their customers by temporarily redirecting them to www.aamarpay.com. The gateway is connecting multiple payment terminal including card system, mobile financial system, local and International wallet . After the payment is complete, the customer is returned to the merchant's site and seconds later the Merchant receives notification about the payment along with the details of the transaction. This document is intended to be utilized by technical personne l supporting the online Merchant's website. Working knowledge of HTML forms or cURL is required. You will probably require test accounts for which you need to open accounts via contact with aamarPay.com or already provided to you. 

### API Operations 

REST AP Is are supported in two environments. Use the Sandbox environment for testing purposes, then move to the live environment for production processing. When testing, generate an order url with your test credentials to make calls to the Sandbox URIs. When you’ re set to go live, use the live credentials assigned to your new signature key to generate a live order url to be used with the live URIs .

### For  Post Method in json  You need to the calling url as below

●  Sandbox (for testing) :  https:// sandbox .aamarpay.com/ jsonpost.php

●  Live (production) :  https://secure.aamarpay.com / jsonpost.php

### Variables Need to Post to Initialize Payment Process Order URL

![image](https://github.com/user-attachments/assets/f5ba73a3-560a-484f-a549-d7e97587842b)

![image](https://github.com/user-attachments/assets/ead905f4-a3ea-4c4d-8e72-5265fa62df94)

#### Example Using Postman

![image](https://github.com/user-attachments/assets/e0f69b67-2ad9-4494-b724-1375ef92823d)

#### You will be get payment URL with the json response as like below 
screenshot

![image](https://github.com/user-attachments/assets/4f031eb5-cd91-419b-854d-fac562e80e4c)

When customer redirect with payment URL then customer will get the 
all payment method as below screenshot
Note: For sandbox only bKash payment method is available, when you 
initiate payment with live you will get all payment method.

Sandbox Payment Method UI after redirecting payment URL

![image](https://github.com/user-attachments/assets/bc8714b0-aae8-41c1-8ef5-792c90a458a2)

Live Payment method UI after redirecting live payment URL
Card Options

![image](https://github.com/user-attachments/assets/a39faaaa-bfd3-455a-9b89-cd83c2533c5f)

MFS Options

![image](https://github.com/user-attachments/assets/5a545fc5-1662-424c-abf8-f5b59994cc53)

After successful payment client will redirect your success page which you are 
already passing in our payment gateway as success_url and aamarPay will give 
you all data as POST method in your success_url
All return variable given below:

```javascript
{
    pg_service_charge_bdt:  "0.21", 
    pg_service_charge_usd:  "Not- A vailable", 
    pg_card_bank_name:  "", 
    pg_card_bank_country:  "", 
    card_number:  "01826323538", 
    card_holder:  "", 
    cus_phone:  "0111", 
    desc:  "", 
    success_url:  "h ttp://localhost/aamarpay/callback/success.php" , fail_url:  "h ttps://example.com/fail" , 
    cus_name:  "imtiaz", 
    cus_email:  "imtiaz@gmail.com", 
    currency_merchant:  "BDT", 
    convertion_rate:  "", 
    ip_address:  "103.228.202.73", 
    other_currency:  "10.00", 
    pay_status:  "Successful", 
    pg_txnid:  "AAM1604470136103451", 
    epw_txnid:  "AAM1604470136103451", 
    mer_txnid:  "asdkfljaw34543", 
    store_id:  "aamarpaytest", 
    merchant_id:  "aamarpaytest", 
    currency:  "BDT", 
    store_am ount:  "9.79", 
    pay_time:  "2020- 1 1- 0 4 12:09:15", amount:  "10.00", 
    bank_txn:  "6ED4FIJ1G0", 
    card_type:  "bKash- b Kash", 
    reason:  "", 
    pg_card_risklevel:  "", 
    pg_error_code_details:  "", 
    opt_a:  "test", 
    opt_b:  "1234234", 
    opt_c:  "", 
    opt_d:  ""
}
```

Same data you will be get  as a POST method in your fail_url when the transaction is failed.
Note: We do not submit any data in cancel_url, it will be your product page link or your home page link.




# AAMARPAY PAYMENT GATEWAY
Excepted Work Flow of Aamarpay Payment gateway
![image](https://github.com/user-attachments/assets/7a05abea-b015-4de4-a378-ba9d7654e0fa)

- Client send a request to server to make a payment with Aamarpay payment gateway.
- Server connects with Aamarpay with the information which is provided by client and
create a payment url.
- Aamarpay payment gateway returns the response with transaction id and payment url.
- 
![image](https://github.com/user-attachments/assets/c253fdc1-bf9a-48e3-94e3-366ce5883255)

- After getting the payment url response, server forward this response to the client side.
- Whenever the response received from server with the payment url, Client will try to build
the widget from the url which is reserved from the server.
- Once widget is build by client it will provide options to the user such as Netbanking,
credit/debit cards etc., User will do select the appropriate method and try to complete
the transaction.
- Once the transaction is completed based on the respective transaction status Aamarpay
payment gateway is redirecting to the respective success, failure or cancel url.
- But the problem which is there in the current system is instead of redirecting to the
respective success/failure/cancel url it is doing a post request. Below mentioned
flowchart we've highlighted in red color which is the problematic area for our
microservice based application.


Hence we are considering that the Aamarpay payment gateway is not best fit for the
microservices based architecture.

![image](https://github.com/user-attachments/assets/535ff1fb-e541-49dc-b288-60514c74d1c8)

