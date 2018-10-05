# Configuration

Various settings can be retrieved post login.

<aside class="notice">
Certain functionality needs to be able to be enabled for a user for example the Agent Terminal, Forex, dependent on Feature Flags.
</aside>

## Fetch configuration for user

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/users/d19bff36-4733-11e5-946b-9ba904d8238e/config"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
    "status": "ok",
    "details": {
        "features": {
            "agentterminal": true,
            "forex": false,
            "prepaid": true,
            "prepaid_airtime": true,
            "prepaid_electricity": false
        }
    }
}

This endpoint retrieves the configuration for the specific user.

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/users/<USER>/config`

### URL Parameters

Parameter | Description
--------- | -----------
USER | The UUID of the user whose config you would like to retrieve

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
features.agentterminal | boolean | Whether user should have access to the agent terminal (being added in a later build of the app)
features.forex | boolean | Whether user should have to the forex functionality
features.prepaid | boolean | Whether user should have access to the prepaid items
features.prepaid_airtime | boolean | Whether user should have access to buying prepaid airtime
features.prepaid_electricity | boolean | Whether user should have access to buying prepaid electricity