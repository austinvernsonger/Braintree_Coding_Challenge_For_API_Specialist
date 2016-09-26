# Braintree Coding Challenge for API Specialist

## Questions to Answer

1. I just launched my official NBA Bulls merchandise business and started taking orders this week. 
  - I had a customer reach out to me to say that they couldn't pay. 
  - What's weird is that the customer sees a charge from us on their bank account online. 
  - Why did that happen, and can it be prevented?

A: Well if it's new customer and the customer saves their credit card information, braintree must verify that credit card before  storing that information in the vault and charging that card when the customer purchase something. The gateway verifies credit cards by running either a $0 or $1 authorization and then automatically voiding it. Some banks don't recognize void requests immediately. It's possible that after you/I(merchant) issue the void, the customer will still see the pending charge. 
If this happens, the customer needs call their bank; the bank should be able to see the void request and update the customer's bank statement accordingly.

NOTE: There are probably rare occurrences where a webhook trigger, fires improperly. 

2. I've also had a few other customers pay today and I noticed their transactions have a status of Submitted for Settlement. What does that mean, and when will I get the money from those orders?

A: The transaction has been submitted for settlement and will be included in the next settlement batch. Settlement happens nightly – the exact time depends on the processor.


## Requirements

- Use JavaScript Version 2.
- The client-side code needs to request a client token from the server, make a braintree.setup call to configure Hosted Fields, and finally present a payment form that uses Hosted Fields.  
- Upon submission, the form should submit a payment method nonce to the server.
- On the server side, please make two API calls. The first should use this nonce to verify the card and store it in your vault, and the second should create a transaction using this stored payment method.
- The integration should provide feedback indicating whether the transaction was successful or not.


## CHANGELOG

### [0.0.1] - 2016-SEP-26
#### Added
- Added custom css input wrappers for card-number, cvv, expiration-month, expiration-year, postal-code
- Added braintree.setup call for hosted fields on file "new.html"
- Added Questions for writing prompt to README

#### Remove
- Removed "amount" input so the price couldn't be changed.
- Removed JavaScript regarding "payment-form"
- Removed hyperlink to Drop-in guide

#### changed
- Changed pseudoshop to Braintree Coding Challenge for API Specialist


## References
https://developers.braintreepayments.com/
https://developers.braintreepayments.com/start/overview#client-token
https://developers.braintreepayments.com/guides/hosted-fields/setup-and-integration/javascript/v2#braintree.setup
https://developers.braintreepayments.com/guides/hosted-fields/setup-and-integration/javascript/v2#basic-integration
https://developers.braintreepayments.com/start/overview#payment-method-nonce
https://developers.braintreepayments.com/guides/payment-methods#create
https://developers.braintreepayments.com/guides/transactions
