# Companies

Refactoring companies on the banking platform is on hold for other tasks at present.  In the future a company
will have seperate beneficiaries.

## List Companies User has Access To

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/companies"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "details": [
    {
      "uuid": "ddfa9e8a-e6c6-11e5-826b-f733da52efd0",
      "name": "KESTA GROUP",
      "trading_as": "KESTA GROUP"
    },
    {
      "uuid": "91654406-071b-11e6-8598-0fffdf7fc583",
      "name": "KESTA Dup",
      "trading_as": "KESTA"
    }
  ]
}
```

## Get Company

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/companies/ddfa9e8a-e6c6-11e5-826b-f733da52efd0"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```
{
  "status": "ok",
  "details": {
    "uuid": "ddfa9e8a-e6c6-11e5-826b-f733da52efd0",
    "name": "KESTA GROUP",
    "trading_as": "KESTA GROUP"
  }
}
```
