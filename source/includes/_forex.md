# Forex

There are a number of things to cater for with Forex.

 * Destination countries coming online.  For the testing of the app we are using:
    - Bangladesh
    - Botswana
    - Kenya

## List Forex Recipients


## Registering a Forex Receipient

This endpoint retrieves a collection of recipients including their status of whether the recipient has
been approved for receiving forex.  Only approved users can receive forex so users in the pending state
are pending approval (i.e. KYC / AML checks), users in approved status have been approved and users who
are in the declined status have been declined.

### HTTP Request

`POST https://127.0.0.1.xip.io/api/v1/mobile/users/<USER>/forex/recipients`

### URL Parameters

Parameter | Description
--------- | -----------
USER | The UUID of the user who you want to register the forex recipient against

### JSON Payload Parameters

Parameter | Type | Description
--------- | ---- | -----------
country   | string(2) | ISO Country Code (i.e. BD for Bangladesh)
account_number | numberic | Account Number of the Recipient
currency_code | string(3) | ISO Currency Code (i.e. BDT for Bangladeshi Taka)
address_street1 | string(255) | Address
address_street2 | string(255) | Address
city | string(255) | City
postal_code | string(255) | Postal Code
first_name | string(64)
middle_name | string(64)
surname | string(64)
date_of_birth | date | ISO DATE (i.e YYYY-MM-DD)
primary_identification_number | string(255) |
passport_number | string(255) |
passport_expiry_date | date | (i.e. YYYY-MM-DD)
passport_issue_country | string(3) | Country which issued the passport
primary_mobile_number | string(32) | Primary Mobile Number of the user (i.e. 27821234567 without a +)
deposit_taker | string(36) | UUID of the deposit taker configured on Plutus
iban | string(255) | IBAN for the account

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
uuid | string (36) | UUID of the wallet

## Uploading a Forex Recipients Documentation

For a recipient to be able to receive a remittance, we need to have various documents uploaded for vetting by our Forex Team as well as the Forex Maker, Reserve Bank, etc. as well as for Anti Money Laundering (AML) purposes.
