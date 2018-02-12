# Person to Person Payments

Person to Person Payments are used to make a once off payment to another person
who has an account on the platform from one onnet account to another onnet
account.

## Perform a P2P Payment

```shell
curl -X POST "https://127.0.0.1.xip.io/api/v1/users/d19bff36-4733-11e5-946b-9ba904d8238e/p2ppayments/process"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "details":
    {
      "name": "Bob",
      "branch_code": "000000",
      "account_number": "12345678910",
      "my_reference": "Bob",
      "their_reference": "Cliff"
    }
  ]
}
```

This endpoint performs a p2p payment from one onnet account to another onnet account.

### HTTP Request

`POST https://127.0.0.1.xip.io/api/v1/users/<USER>/beneficiaries`

### URL Parameters

Parameter | Description
--------- | -----------
USER | The UUID of the user the beneficiary belongs to

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
name      | string(32) | Users name for the recipient (i.e. Telkom - Home Phone)
account_number | integer | Bank Account Number for the beneficiary typically 9 to 11 digits in length
reference1 | string(32) | Users reference for their account transaction list when making the payment
reference2 | string(32) | Reference displayed on the beneficiaries bank transaction list
