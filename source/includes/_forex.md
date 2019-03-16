# Forex

<aside class="notice">
Please note: Plutus does not do any forex processing.  This is handled outside of the platform.  The payment from a users account to pay their forex transaction moves money
from their wallet and into our SFX processing account.
</aside>

## Pay for a Forex Transaction

<aside class="warning">
Work in Progress
</aside>

## Registering a Forex Receipient

```shell
curl -X POST "https://127.0.0.1.xip.io/api/v1/mobile/users/c3797604-6e78-486e-be5d-433f80cc4993/payments/forex"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
  -d '{"first_name":"Joe","last_name":"Soap","country":"ZAF","account_number":"12345678912","deposit_taker_swift":"TESTZAJJ"}'
```

This endpoint adds a forex recipient to a users account.

When a user specifies a collectionpoint as the destination_type then they will receive a SMS once Andre has loaded the forex
transaction onto the vendors system and a quote is given and accepted for the user to send the reference number to the
recipient to use when collecting the remittance.

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
destination_type | enum | bank or collection point -- note a wallet type is coming once Andre gets the specification for it.
account_number | numeric | Account Number of the Recipient
deposit_taker_swift | string(16) | SWIFT Code of the Deposit Taker

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
uuid | string (36) | UUID of the recipient
