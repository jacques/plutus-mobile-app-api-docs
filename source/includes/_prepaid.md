# Prepaid Services

The Platform provides clients with the ability to purchase prepaid airtime and electricity.

Refunds are not supported on prepaid purchases.  Should the mobile network for example fail to vend the voucher the money is returned during a 24 hour period.

There are a number of different offerings on offer.

## List mobile networks

Retreives a list of mobile network providers and fixed line providers who vend
Prepaid Airtime Vouchers or Pinless Airtime Recharges.

```shell
curl "https://127.0.0.1.xip.io/api/v1/prepaid/networks"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

```json
{
  "status": "ok",
  "data": [
    {
       "network_id": "1",
       "name": "Vodacom"
    },
    {
       "network_id": "2",
       "name": "MTN"
    },
    {
       "network_id": "3",
       "name": "CellC"
    },
    {
       "network_id": "4",
       "name": "Virgin Mobile"
    },
    {
       "network_id": "5",
       "name": "Neotel"
    },
    {
       "network_id": "6",
       "name": "Telkom Mobile (8ta)"
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
network_id | integer | ID for the mobile network
name | string(36) | Name of the mobile network or virtual mobile network operator

## List available vouchers for a network

Retreive a list of available airtime vouchers for the provide mobile network.




## Purchase Prepaid Airtime

## List of Prepaid Airtime Networks Available

## Purchase Prepaid BongoTel Airtime

Allows a user to rechange their BongoTel phone airtime.

## Purchase Prepaid Electricity

Purchases prepaid electricity for the provided meter number.  Please note that the current provider does not allow for prevending or meter information lookups.



Text needs to be displayed that states "All vends are final.  Municipalities and Eskom do not allow reversals on the sale of Electricity.  Electricity is not sold subject to a cooling off period."

(Check with Tim on the wording for this).



