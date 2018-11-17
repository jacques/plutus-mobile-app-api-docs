# Authentication

<aside class="notice">
If a user has been logged out on the platform (i.e. we have locked the users account) the users token will no longer be valid.
A HTTP Status code 401 is returned with the body containing HTTP Token: Access denied.  The state should change to the user
not being logged into the mobile application.
</aside>

## Intial Login for a user

Authenticate as a user to the Mobile APP API.  This replaces the more secure HTTP Signature method.

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl -X POST "api_endpoint_here"
  -H "Authorization: Token token=YOURTOKEN"
  -H "Content-Type: application/json"
  -d '{"username":"theuser12345":"password":"abcdefgh"}'
```





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
