# Ads

On the mobile application, various ads are displayed to show features that are
available to the user or promotions being targeted at the user for them to
opt-into.

For example we have multiple ad slots:

 * 1 - Show Remit home to Bangladesh (forex controller)
 * 2 - Show Buy a Mastercard
 * 3 - Show Buy Airtime
 * 4 - Show RICA
 * 5 - Signup for BongoTel

etc.

## List Adverts for a User

```shell
curl "https://127.0.0.1.xip.io/api/v1/mobile/users/d19bff36-4733-11e5-946b-9ba904d8238e/ads"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

```json
{
    "status": "ok",
    "details": [
        {
            "image": "https://secure.imogo.co.za/images/mobileapp/ads/prepaid-airtime-v1.jpg",
            "type": "app",
            "destination": "PrepaidAirtime#index"
        },
        {
            "image": "https://secure.imogo.co.za/images/mobileapp/ads/introducing-bongotel-v1.jpg",
            "type": "webview",
            "destination": "https://secure.imogo.co.za/mobilepromo/introducing-bongotel"
        }
    ]
}
```

This endpoint retrieves a collection of adverts which should be shown to the specific user.
The assumption is we can call the controller being used in the mobile app like Controller#action.

### HTTP Request

`GET https://127.0.0.1.xip.io/api/v1/mobile/users/<USER>/ads`

### URL Parameters

Parameter | Description
--------- | -----------
USER | The UUID of the user whose ads you would like to retrieve

### Response Result Set

Parameter | Type | Description
--------- | ---- | -----------
image | string (255) | URL to image
type | enum | webview / app
destination | string (255) | URL to link to for opening in a web view

@Leon can we differentiate between webviews and app (i.e. go to Prepaid?)
