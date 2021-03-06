# Business Accounts

There are numerous types of business accounts.

 * business = normal business account
 * merchant = rules around funds release from TPPP's (i.e. PayFast) before money clears

## Get Business Accounts belonging to Company

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/companies/ddfa9e8a-e6c6-11e5-826b-f733da52efd0/accounts"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "details": [
    {
      "uuid": "5821ff12-e9f3-11e5-88e9-cb402de15a2b",
      "account_number": "53216141969",
      "description": "KESTA - DANNY Business Account",
      "account_type": "business",
      "currency": 710,
      "balance": 4620
    }
  ]
}
```

## Get Business Accounts Transactions belonging to Company

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/companies/ddfa9e8a-e6c6-11e5-826b-f733da52efd0/accounts/5821ff12-e9f3-11e5-88e9-cb402de15a2b"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "details": {
    "account": {
      "account_number": "53216141969",
      "uuid": "5821ff12-e9f3-11e5-88e9-cb402de15a2b",
      "description": "KESTA - DANNY Business Account",
      "account_type": "business",
      "balance": 4620
    },
    "transactions": [
      {
        "txn_ref": "riubyn8m",
        "statement_date": "2016-03-23",
        "reference1": "SO PROC PAYMENT FROM",
        "reference2": "53222423658",
        "amount": 1000
      }
    ]
  }
}
```
