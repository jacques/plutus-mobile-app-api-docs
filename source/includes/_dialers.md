# Dialers

The BongoTel Dialer allows users to make affordable calls using the BongoTel Platform.

## List Dialers

```shell
curl -X GET "https://127.0.0.1.xip.io/api/v1/mobile/dialers"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
  -d '{"title":"MRS","first_name":"CHERYL","last_name":"SERFONTEIN","date_of_birth":"1970-01-01","gender":"f","id_type":"ZAID","id_document_number":"7001010101081","address1_type":"work","address1_street1":"7th Floor, West Tower, Canal Walk Shopping Center","address1_street2":"Century City Boulevard, Century City","address1_suburb":"Milnerton","address1_city":"Cape Town","address1_province":"ZA-WC","address1_postalcode":"7490","address1_country":"ZA",mobile_number":"08012345679"}'
```

> The above command returns JSON structured like this:

```json
{
  "status":"ok",
  "details":{
    "uuid":"2b1c1f24-c5ff-11e5-99c3-5a8f9bcf73ec",
    "account_number":"53224172946"
  }
}
```
This endpoint creates a new customer on the ##BRAND## Platform.  During the process a wallet is created for the customer.


## Issue Dialer
