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
first_name | string(64)
middle_name | string(64)
last_name | string(64)
country   | string(2) | ISO Country Code (i.e. BD for Bangladesh)
account_number | numberic | Account Number of the Recipient
currency_code | string(3) | ISO Currency Code (i.e. BDT for Bangladeshi Taka)
address_street1 | string(255) | Address
address_street2 | string(255) | Address
city | string(255) | City
postal_code | string(255) | Postal Code
date_of_birth | date | ISO DATE (i.e YYYY-MM-DD)
birth_city | string(255) | City of birth
birth_country | string(2) | ISO Country Code (i.e. BD for Bangladesh)
primary_identification_number | string(255) |
passport_number | string(255) |
passport_expiry_date | date | (i.e. YYYY-MM-DD)
passport_issue_country | string(3) | Country which issued the passport
passport_line_1 | string(255) | Machine Readable Zone Line 1
passport_line_2 | string(255) | Machine Readable Zone Line 2
primary_mobile_number | string(32) | Primary Mobile Number of the user (i.e. 27821234567 without a +)
deposit_taker | string(36) | UUID of the deposit taker configured on Plutus
deposit_taker_swift | string(16) | SWIFT Code of the Deposit Taker
iban | string(255) | IBAN for the account
name_of_father | string(255) | Name of father
name_of_mother | string(255) | Name of mother i.e. Jane Soap nee Doe
name_of_spouse | string(255) | Name of spouse
profession | string(255) | Profession of the recipient
employer_name | string(255) | Name of the current employer
employer_contact_name | string(255) | Name of the contact at the current employer
employer_contact_number | string(32) | Phone number for the current employer contact person
previous_employer_name | string(255) | Name of the previous employer
previous_employer_contact_name | string(255) | Name of the contact at the previous employer
previous_employer_contact_number | string(32) | Phone number for the previous employer contact person

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
uuid | string (36) | UUID of the recipient

## Uploading a Forex Recipients Documentation

For a recipient to be able to receive a remittance, we need to have various documents uploaded for vetting by our Forex Team as well as the Forex Maker, Reserve Bank, etc. as well as for Anti Money Laundering (AML) purposes.
