# Okta Client Credential Flow Example

Based on Okta [Client Credential Flow](https://developer.okta.com/authentication-guide/implementing-authentication/client-creds) docs:

1. If new account is required: from [Okta Developer Page](https://developer.okta.com/), click "sign up" button and create a free developer okta account, I created:
    ```
    User name: mkozi.okta01@gmail.com
    Okta URL: https://dev-489531.oktapreview.com (use this to login)
    Company: mkoziokta
    Account: mkoziokta-dev-489531
    See KeePass for 'Okta 3'
    ```
2. Login to Okta at Okta URL listed above
3. Create a new Application:
    * Click on "Applications -> Applications" 
    * Click on "Add Application"
    * Click on "Create New App"
    * Select "OAuth Service"
    * Select "Create"
    * Enter a name and click "Save"
4. Create custom Scope (from Okta website - [Create Scopes](https://developer.okta.com/authentication-guide/implementing-authentication/set-up-authz-server#create-scopes-optional) instructions):
5. Use postman to get a token:
    Type: POST
    Url: https://dev-489531.oktapreview.com/oauth2/default/v1/token
    Headers:
        Accept: application/json
        Content-Type: application/x-www-form-urlencoded
        Authorization: <HTTP Basic Auth encoded client_id:client_secret>
        Cache-Control: no-cache
        
    Response contains a encoded JWT token - use [jsonwebtoken.io](https://www.jsonwebtoken.io) to view access token
    
    Note:  It is vital to [Validate](https://developer.okta.com/authentication-guide/tokens/validating-access-tokens) access tokens before using them, including:
        * verify correct audience
        * verify correct issuer
        * verify correct client id
        * check validity of expiration date
        * verify that the payload is correctly signed with the included signature
