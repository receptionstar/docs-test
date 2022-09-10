---
title: API Authentication
nav_order: 2
---


# API Authentication

The Reception Star API uses "short-lived" OAuth 2.0 tokens for authentication that expire after 3 hours.

When you request an access token, you'll be provided with a _refresh token_ and an _expiry offset_, which is the number of seconds until the token expires.

Using the _expiry offet_, you know when your access token will not be valid, so that if needed, you can proactively create a CRON job that refreshes the access tokens, or wrap your HTTP requests in an exception handler that looks for `Not Authorized` error and the refreshes them as the OAuth 2.0 spec recommends.

When interacting with the API, you will need to first authenticate to request an access token.


## Examples

### POST authorize

```
curl -X GET \
  https://my.receptionstar.com/api/v1/auth
```

### Response 200

```js
{ "token":"YOUR_ACCESS_TOKEN" }
```

### Response 401

This could be due to any of the following, noted in the response:

- the user doesn't exist, 
- the password is incorrect, 
- the password is reported as being pwned, or 
- the token is expired, 

