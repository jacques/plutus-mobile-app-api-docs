# Configuration

Various settings can be retreived post login.

<aside class="notice">
Certain functionality needs to be able to be enabled for a user for example the Agent Terminal, Forex, dependant on Feature Flags.
</aside>

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
