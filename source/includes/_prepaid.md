# Prepaid Services

The Platform provides clients with the ability to purchase prepaid airtime and electricity.

Refunds are not supported on prepaid purchases.  Should the mobile network for example fail to vend the voucher the money is returned during a 24 hour period.

There are a number of different offerings on offer.

## List mobile networks

Retreives a list of mobile network providers and fixed line providers who vend
Prepaid Airtime Vouchers or Pinless Airtime Recharges.  Logos to be supplied
by Danny.

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/prepaid/networks"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

```json
{
  "status": "ok",
  "data": [
    {
       "network": "vodacom",
       "name": "Vodacom",
       "image": "/images/mobiapp/vodacom.jpg"
    },
    {
       "network": "mtn",
       "name": "MTN",
       "image": "/images/mobiapp/mtn.png"
    },
    {
       "network": "cellc",
       "name": "CellC",
       "image": "/images/mobiapp/cellc.png"
    },
    {
       "network": "virginmobile",
       "name": "Virgin Mobile",
       "image": "/images/mobiapp/virginmobile.png"
    }
  ]
}
```

This endpoint retrieves the list of mobile networks.

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/prepaid/networks`

### Response Result Set

Parameter | Type | Description
--------- | ----  | -----------
network | string(16) | Shortname for network
name | string(36) | Name of the mobile network or virtual mobile network operator
image | string(36) | Image for the logo of the mobile network for use with resizing of the logo

## List available vouchers for a network

Retreive a list of available airtime vouchers for the provide mobile network.


```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/prepaid/vouchers/vodacom"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

```json
{
  "status": "ok",
  "data": [
    {
      "voucher_code":"VOD000005",
      "description":"Vodacom - R 5",
      "voucher_cost_to_client":"500"
    },
    {
      "voucher_code":"VOD000010",
      "description":"Vodacom - R 10",
      "voucher_cost_to_client":"1000"
    },
    {
      "voucher_code":"VOD000012",
      "description":"Vodacom - R 12",
      "voucher_cost_to_client":"1200"
    }
  ]
}
```

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/prepaid/vouchers/<NETWORK>`

### Response Result Set

Parameter | Type | Description
--------- | ----  | -----------
network | string(16) | Shortname for network
name | string(36) | Name of the mobile network or virtual mobile network operator
image | string(36) | Image for the logo of the mobile network for use with resizing of the logo


## Purchase Prepaid Airtime

## List of Prepaid Airtime Networks Available

## Purchase Prepaid Electricity

Purchases prepaid electricity for the provided meter number.  Please note that the current provider does not allow for prevending or meter information lookups.

Text needs to be displayed that states "All vends are final.  Municipalities and Eskom do not allow reversals on the sale of Electricity.  Electricity is not sold subject to a cooling off period."

(Check with Tim on the wording for this).
