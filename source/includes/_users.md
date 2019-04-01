# Users

## User Creation

Creates a user on the platform.  It issues the newly created user with a wallet.  The user needs to still to go through the
FICA process if it is not a product specific wallet (i.e. for the dialler product for purchasing airtime).  If the user
requires normal wallet functionality to receive and spend via multiple partners this still needs to be story boarded with
Tim.

<aside class="notice">
Creating a user does not require authentication.
</aside>

```shell
curl -X POST "https://127.0.0.1.xip.io/api/v1/mobile/users"
  -H "Content-Type: application/json"
  -d '{"title":"MRS","first_name":"CHERYL","last_name":"SERFONTEIN","date_of_birth":"1970-01-01","gender":"f","id_type":"ZAID","id_document_number":"7001010101081","address1_type":"work","address1_street1":"7th Floor, West Tower, Canal Walk Shopping Center","address1_street2":"Century City Boulevard, Century City","address1_suburb":"Milnerton","address1_city":"Cape Town","address1_province":"ZA-WC","address1_postalcode":"7490","address1_country":"ZA",mobile_number":"08012345679"}'
```

> The above command returns JSON structured like this:

```json
{
  "status":"ok",
  "details":{
    "uuid":"2b1c1f24-c5ff-11e5-99c3-5a8f9bcf73ec",
    "account_number":"53224172946",
    "username": "timot12345",
    "password": "badcaffe"
  }
}
```
This endpoint creates a new customer on the ##BRAND## Platform.  During the process a wallet is created for the customer.

### HTTP Request

`POST https://127.0.0.1.xip.io/api/v1/mobile/users`


### JSON Payload Parameters

Parameter | Type | Description
--------- | ---- | -----------
title | string (4) | Title of the user (i.e. MR / MRS / MS / DR / PROF)
first_name | string (64) | First names of the user
last_name | string (64) | Surname of the user
date_of_birth | date | Date of birth of the user
gender | string (1) | Gender of the user (i.e. f == female / m == male)
id_type | string | Identification Document Type (ZAID == South African ID / PASSPORT = Passport / ZAASYLUM = South African Asylum Document)
id_document_number | string (32) | The document number for the given identification type
passport_start_date | date | Date of the start of the passport **REQUIRED IF id_type IS PASSPORT** (required by FNB)
passport_expiration_date | date | Date of expiration of the passport **REQUIRED IF id_type IS PASSPORT**
passport_country | string (2) | [ISO 3166 Alpha 2 code](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) for the country **REQUIRED IF id_type IS PASSPORT**
asylum_start_date | date | Date of the start of the South African Asylum Document **REQUIRED IF id_type IS ZAASYLUM** (required by FNB)
asylum_expiration_date | date | Date of expiration of the South African Asylum Document **REQUIRED IF id_type IS ZAASYLUM**
address1_type | enum | **home** for home address / **work** for employers address.  Users should be FICA's to their home addresses.
address1_street1 | string (64) | Street Address
address1_street2 | string (64) | Street Address cont. **OPTIONAL**
address1_suburb | string (64) | Suburb
address1_city | string (64) | Name of the City or Town
address1_province | string (6) | [ISO 3166-2 ZA code](https://en.wikipedia.org/wiki/ISO_3166-2:ZA)
address1_postalcode | string (4) | Postal Codes for South Africa
address1_country | string (2) | [ISO 3166 Alpha 2 code](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) for the country
mobile_number | integer | MSISDN for the user in E.164 format (minus the leading +)
email_address | string(64) | Email address of the user
nationality | string(2) | [ISO 3166 Alpha 2 code](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) for the nationality of the user (required by FNB)
ethnic_group | integer | (1 = White | 2 = Asian | 3 = Coloured | 4 = Black | 5 = Unknown) (required by FNB)

### Defaults (optional parameters)

Parameter | Type | Default | Description
--------- | ---- | ------- | -----------
assign_to_agent | string(36) | null | Specifies which agent should be assigned to the user being created
promocode | string(36)| null | Specifies the promo code to use when the user is created.  This is used to change the agency (i.e. register the user under a specific agents structure).
