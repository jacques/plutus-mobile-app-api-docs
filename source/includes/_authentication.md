# Authentication

## Intial Login for a user

After installing the mobile app, a user would request that they be allowed to login using their credentials.  On first login, a ssh keypair
is generated on the users device and the public key pair is submitted along with the fingerprint over which is then associated with the user.
Should the user have Two Factor Authentication enabled, the user will then enter their TFA to authorise the adding of the ssh key pair to
their account.

## Using Session Tokens

Pass in the `Authorization` header in with a `Token token=YOURTOKEN` as part of the HTTP request being sent into the API for processing once you have
created a session token for the user.

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
```

> Make sure to replace `YOURTOKEN` with your API key.

The Plutus Platform uses API keys to allow access to the API. You can register a new Plutus Platform API key via your Sales Manager.

Plutus expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token token=YOURTOKEN`

<aside class="notice">
You must replace <code>YOURTOKEN</code> with your program API key.
</aside>

<aside class="notice">
Please do not share your Plutus Platform credentials as they unlock sensitive resources, such as transaction histories for your customers and can perform instructions your apps receive on behalf of a customer such as making payments.
</aside>
