# Forex

Forex recipients are now a manual process.  This will change at a later date to
using an API to the forex supplier.

Initially we are supporting sending to a bank account.  Later once we have information support for sending to a destination cashpoint or another wallet provider is going to be supported.

<aside class="notice">
For transactions going to a cash point, Andre says the sender is SMS'ed a
reference number for the recipient to be sent to collect the money from
any of the cash points in the country.
</aside>

<aside class="notice">
Need to look at getting GPS co-ordinates of where the transaction occurred for Forex.
</aside>

<aside class="notice">
Wallet providers is also pending from Andre.  Nothing has been provided for this option.  Not enabling this option via the API.
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
last_name | string (255) | Surname of the recipient

## Registering a Forex Receipient

```shell
curl -X POST "https://127.0.0.1.xip.io/api/v1/mobile/users/c3797604-6e78-486e-be5d-433f80cc4993/forex"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
  -d '{"first_name":"Joe","last_name":"Soap","country":"ZAF","account_number":"12345678912","deposit_taker_swift":"TESTZAJJ"}'
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
last_name | string(64)
country   | string(2) | ISO Country Code (i.e. BD for Bangladesh)
mobile_number | integer | MSISDN of the recipient in E164 format minus the leading +
account_number | numeric | Account Number of the Recipient
deposit_taker_swift | string(16) | SWIFT Code of the Deposit Taker

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
uuid | string (36) | UUID of the recipient