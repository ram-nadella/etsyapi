The Etsy API
============

API Basics
-------------

This is temporary documentation for V3 of the Etsy API.
See the [API Reference](REFERENCE.md) for information regarding
specific API calls.

### Base URL

The base URL for the Etsy API is:
```
https://openapi.etsy.com/v3/
```
All paths should be added after that. Note that HTTPS is **required**;

### Submit the API Key

The API key is submitted as in the `x-api-key` HTTP header.
If the API key is 'ABC789', then submit a header as:
```
x-api-key: ABC789
```

### Submit the OAuth Token

We use OAuth 2 bearer tokens which are submitted in the Authorization header.
If the OAuth token is 'xyz123', then submit the header as:
```
Authorization: Bearer xyz123
```

Perspectives
-------------------

The Etsy API has a concept of _perspectives_ which indicates on whose behalf
a request is being made.

### Public Perspective

```
https://openapi.etsy.com/v3/public
```

The Public Perspective is for data that is visible to signed out user.
An example of this would be a shop banner.

### Member Perspective

```
https://openapi.etsy.com/v3/member
```

Member Perspective calls require an OAuth token and are made on behalf
of the user who authorized that token. This perspective might be used
to retrieve the email address of a user.

### Shop Perspective

```
https://openapi.etsy.com/v3/shop/:shop_id
```

Shop Perspective calls also require an OAuth token and are made on behalf
of the given shop (assuming it is owned by the user who authorized the
given oauth token). This perspective could be used to renew a listing
owned by the shop.

### Application Perspective

```
https://openapi.etsy.com/v3/application
```

The Application Perspective is to make private calls on behalf of your
own application. An example of this is to add provisional users if your
app doesn't have or need full access.
