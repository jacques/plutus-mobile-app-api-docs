# Forex

There are a number of things to cater for with Forex.

 * Destination countries coming online.  For the testing of the app we are using:
    - Bangladesh (BD)
    - Botswana (BW)
    - Malawi (MW)
    - Mozambique (MZ)
    - Zimbabwe (ZW)

## List Forex Recipients

```shell
curl -X GET "https://127.0.0.1.xip.io/api/v1/mobile/users/c3797604-6e78-486e-be5d-433f80cc4993/forex"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

This endpoint retrieves a collection of recipients for sending forex to.  These users have been
added as recipients for the user.

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/users/<USER>/forex/recipients`

> The above command returns JSON structured like this:

```json
{
  "status":"ok",
  "details":[
    {
      "uuid":"72d11c48-a565-4731-8915-462084ee0a9f",
      "first_name":"Timothy",
      "middle_name":"Michael",
      "last_name":"Colman"
    }
  ]
}
```

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
uuid | string (36) | UUID of the document
first_name | string (255) | First name of the recipient
middle_name | string (255) | Middle name of the recipient
last_name | string (255) | Surname of the recipient

## Registering a Forex Receipient

```shell
curl -X POST "https://127.0.0.1.xip.io/api/v1/mobile/users/c3797604-6e78-486e-be5d-433f80cc4993/forex"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
  -d '{"first_name":"Joe","middle_name":"Joe","last_name":"Soap","country":"ZAF","account_number":"12345678912","address_street1":"1st Floor, Allianz House","address_street2":"52 St George\'s Mall","city":"Cape Town","postal_code":"8000","date_of_birth":"1969-01-01","birth_country":"ZAF","primary_identification_number":"1234567890123456":"passport_number":"BOB1234","passport_expiry_date":"2020-01-01":"passport_issue_country":"ZAF","passport_line_1":">>>...","passport_line_2":">>>....","primary_mobile_number":"2712345679","deposit_taker":"Test Bank":"deposit_taker_swift":"TESTZAJJ","iban":"TESTZAJJ123456789012","name_of_father":"Tim Soap","name_of_mother":"Gina Soap nee Tutu","name_of_spouse":"Lulu Soap nee Tshwane","profession":"Driver","employer_name":"Example Company","employer_contact_name":"Tim Colman","employer_contact_number":"2721100008","previous_employer_name":"Mr D","previous_employer_contact_name":"Mr Bob","previous_employer_contact_number":"27111111111"}'
```

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

```shell
curl -X POST "https://127.0.0.1.xip.io/api/v1/users/d19bff36-4733-11e5-946b-9ba904d8238e/forex/2c4e5c4c-043b-4e1f-82e9-ad506dba2212/documents"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
  -F 'document_type=1'
  -F=@FILE.pdf
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "details": {
    "uuid": "895b2fcc-545f-11e7-8279-67635886d357",
    "document_type": 1,
    "file_name": "55af7356-2641-11e6-9641-51a94b3cc203 - POID - GOVID - Vin Diesel.pdf",
    "file_hash": "4f9ef9c744b05f339b4d74c83a5e98c361ab8a7c35f95532e0ec977e71bfd321",
    "file_size": 3718903,
    "created_at": "2017-06-01 15:33:20"
  }
}
```

This endpoint allows for uploading of documents from a users mobile phone.  The documents are then submitted
for review by the complaince team.  The encoding type needs to be multipart/form-data.  The file needs to be
the equivalent of a input type of file with a name of file:

```html
<form method="POST" enctype="multipart/form-data">
   <input type="file" name="file">
</form>
```

### HTTP Request

`POST https://127.0.0.1.xip.io/api/v1/mobile/users/<USER>/forex/<BENEFICIARY>/documents`

### URL Parameters

Parameter | Description
--------- | -----------
USER | The UUID of the user who you want to upload a document for

### POST Parameters

Parameter | Type | Description
--------- | ---- | -----------
document_type | integer | Indicates the type of document.  See <a href="#document-types">Document Types</a> below.

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
uuid | string (36) | UUID of the document
document_type | integer | Indicates the type of document.  See <a href="#document-types">Document Types</a> below.
file_name | string (255) | File name including a random uuid at the front of the file name
file_hash | string (255) | sha256 of the uploaded file
file_size | integer | Size of the uploaded file
created_at | datetime | Datetime in GMT that the file was uploaded

## List of Target Countries

```shell
curl -X GET "https://127.0.0.1.xip.io/api/v1/mobile/forex/countries"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/forex/countries`

> The above command returns JSON structured like this:

```json
{
  "status":"ok",
  "details":[
    {"country_name":"Bangladesh","tld":"BD"},
    {"country_name":"Botswana","tld":"BW"},
    {"country_name":"Malawi","tld":"MW"},
    {"country_name":"Mozambique","tld":"MZ"},
    {"country_name":"Zimbabwe","tld":"ZW"}
  ]
}
```

## List of Target Banks By Target Country

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/forex/banks/<COUNTRYCODE>`
