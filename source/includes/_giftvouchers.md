# Gift Vouchers

Gift vouchers allow for applying discount rules on product sales.  Presently Gift Vouchers
can only be applied against phone sales and non VAS sales (i.e. buying Airtime or Electricity).

## Listing gift vouchers for a user

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/users/d19bff36-4733-11e5-946b-9ba904d8238e/giftvouchers"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "details": [
    {
      "uuid": "ecb23a8c-99dd-11e4-912d-ef2aab9046d8",
      "description": "Freedom Connect R300 Gift Voucher",
      "currency": "710",
      "amount": "30000",
      "balance": "30000"
    }
  ]
}
```

This endpoint retrieves a collection of gift vouchers belonging to the specific user.

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/users/<USER>/giftvouchers`

### URL Parameters

Parameter | Description
--------- | -----------
USER | The UUID of the user to retrieve

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
uuid | string (36) | UUID of the gift voucher
description | string (64) | Description of the gift voucher
currency | integer | ISO4217 Code Number
amount | integer | value originally provided with the gift voucher in cents
balance | integer | balance of the gift voucher in cents
