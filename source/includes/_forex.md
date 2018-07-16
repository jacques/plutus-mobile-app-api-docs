# Forex

There are a number of things to cater for with Forex.

 * Destination countries coming online.  For the testing of the app we are using:
    - Bangladesh (BD)
    - Botswana (BW)
    - Malawi (MW)
    - Mozambique (MZ)
    - Zimbabwe (ZW)

Destination cashout points pending from Tim which may replace the requirement for a Swift Code
and use a destination location identifier.

<aside class="notice">
Disbursement points pending for specifying rather than banking details where the money is to
be collected (i.e. pick up at a specific shop in Zimbabwe).
</aside>

<aside class="notice">
Need to look at getting GPS co-ordinates of where the transaction occurred for Forex.
</aside>

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
  -d '{"first_name":"Joe","middle_name":"Joe","last_name":"Soap","country":"ZAF","account_number":"12345678912","deposit_taker_swift":"TESTZAJJ"}'
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
deposit_taker_swift | string(16) | SWIFT Code of the Deposit Taker

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

## List of Disbursement Points

<aside class="warning">
Please note Andre has not provided any information on the disbursement points or how this will work.  Needs to be circled back on.
</aside>

## List of Target Banks By Target Country

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/forex/banks/<COUNTRYCODE>`
