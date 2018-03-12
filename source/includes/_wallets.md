# Wallets

Plutus Wallets (accounts) provide a virtual account for depositing of money into one of the Plutus deposit accounts.

The Plutus system uses the following references for allocating money which has been deposited into a users wallet:

Reference|Description
----------|----------
Account Number|Wallet Account Number (i.e. goes into the specified wallet of the user)
South African ID Number|South African issued Identity Document from Home Affairs
MSISDN|MSISDN of the users Mobile Phone Number
Passport Number|Foreigners passport issued by a foreign country
Asylum Document Number|Asylum document issued by Home Affairs to a foreigner

When a user has multiple wallets, the first wallet that was created for the user
would receive the money when the wallets account number is not used in the deposit.

## Listing wallets for a user

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/users/d19bff36-4733-11e5-946b-9ba904d8238e/accounts"
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
      "account_number": "44445555666",
      "description": "Tim's Wallet",
      "account_type": "wallet",
      "currency": "710",
      "balance": "123456"
    }
  ]
}
```

This endpoint retrieves a collection of wallets belonging to the specific user.

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/users/<USER>/accounts`

### URL Parameters

Parameter | Description
--------- | -----------
USER | The UUID of the user to retrieve

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
uuid | string (36) | UUID of the wallet
account_number | integer | Account number for the wallet
description | string (64) | Description of the wallet (i.e Firstname's Wallet)
account_type | enum | `wallet` for wallet
currency | integer | ISO4217 Code Number
balance | integer | balance of the wallet in cents

## Fetching a mini statement for a users wallet


```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/users/d19bff36-4733-11e5-946b-9ba904d8238e/accounts/ecb23a8c-99dd-11e4-912d-ef2aab9046d8/ministatement"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "details": [
    {
      "txn_ref": "alc80075",
      "statement_date": "2015-02-19",
      "reference1": "EFT IN FEE",
      "reference2": "REF: 0801234567",
      "amount": "-90"
    },
    {
      "txn_ref": "61hk1xyo",
      "statement_date": "2015-02-19",
      "reference1": "CREDIT TRANSFER",
      "reference2": "0801234567",
      "amount": "50000"
    },
    ...
  ]
}
```

This endpoint retrieves a mini statement for the specific users wallet.

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/users/<UUID>/accounts/<ACCOUNT>/ministatement`

### URL Parameters

Parameter | Description
--------- | -----------
UUID | The UUID of the user to retrieve
ACCOUNT | The UUID of the account to retrieve

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
txn_ref | string (36) | UUID of the user
statement_date | string (36) | UUID of the user
reference1 | string (32) | Transaction classification
reference2 | string (64) | Narrative of the transaction
amount | integer | Amount of the transaction in cents

## Listing transactions for a users wallet

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/users/d19bff36-4733-11e5-946b-9ba904d8238e/accounts/ecb23a8c-99dd-11e4-912d-ef2aab9046d8/ministatement"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "details": [
    {
      "txn_ref": "alc80075",
      "statement_date": "2015-02-19",
      "reference1": "EFT IN FEE",
      "reference2": "REF: 0801234567",
      "amount": "-90"
    },
    {
      "txn_ref": "61hk1xyo",
      "statement_date": "2015-02-19",
      "reference1": "CREDIT TRANSFER",
      "reference2": "0801234567",
      "amount": "50000"
    },
    ...
  ]
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/users/<UUID>/accounts/<ACCOUNT>/transactions`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
limit | 100 | Specifies the maximum number of users to fetch
offset | 0 | Starts from the first user up to limit users

### URL Parameters

Parameter | Description
--------- | -----------
UUID | The UUID of the user to retrieve
ACCOUNT | The UUID of the account to retrieve

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
txn_ref | string (36) | UUID of the user
statement_date | string (36) | UUID of the user
reference1 | string (32) | Transaction classification
reference2 | string (64) | Narrative of the transaction
amount | integer | Amount of the transaction in cents

## Get an estimate for converting your wallet balance to another currency

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/users/d19bff36-4733-11e5-946b-9ba904d8238e/accounts/ecb23a8c-99dd-11e4-912d-ef2aab9046d8/estimate/BWP"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
    "status": "ok",
    "data": {
        "original": {
            "currency": "ZAR",
            "balance": 100005
        },
        "conversion": {
            "currency": "BWP",
            "amount": 71539
        }
    }
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/users/<UUID>/accounts/<ACCOUNT>/estimate/<CURRENCY>`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
limit | 100 | Specifies the maximum number of users to fetch
offset | 0 | Starts from the first user up to limit users

### URL Parameters

Parameter | Description
--------- | -----------
UUID | The UUID of the user to retrieve
ACCOUNT | The UUID of the account to retrieve
CURRENCY | The currency to convert to

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
currency | string(3) | Currency name
balance | integer | Balance on account
amount | integer | Amount after estimate in requested currency.
