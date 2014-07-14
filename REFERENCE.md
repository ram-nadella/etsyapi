The Etsy API Reference
=========================

Shops
----------------------

#### GET /member/shops

**OAuth Scope:** shops_rw

Retrieve a list of the members shops. If the member has no shops, this
will return an empty array.

Listings
----------------------

#### POST /shop/:shop_id/listings/:listing_id/renew

**OAuth Scope:** listings_w

Renews the listing with the given listing ID.

#### PUT /shop/:shop_id/listings/:listing_id/activate

**OAuth Scope:** listings_w

Sets the given listing to active. Returns 400 if the listing is expired.
In this case the listing must be renewed instead.

#### PUT /shop/:shop_id/listings/:listing_id/deactivate

**OAuth Scope:** listings_w

Sets the given listing to inactive.

#### DELETE /shop/:shop_id/listings/:listing_id

**OAuth Scope:** listings_w

Deletes the given listing.

Countries
----------------------

#### GET /public/countries

Retrieve a list of all countries with some additional data.

#### GET /public/countries/:country_id

Retrieve data for a single country.

:country_id can be an integer country ID or a two letter ISO country code

Provisional Users
----------------------

Applications that do not need or do not yet have Full Access can,
by default, authenticate only for the user who owns the application.
It was possible to add additional users, "Provisional Users", but
required emailing Etsy and we would do it manually. Now this is
available to application developers to manage directly via the
Provisional Users API calls.

#### GET /application/provisional-users

Returns all provisional users currently added for your application.
Initially, this will be an empty list, []. This list does not include
the user who owns the application, so seeing an empty list does not
indicate that you can no longer authenticate as the application owner.

#### POST /application/provisional-users/:user_id

Submit this request as a POST, and replace :user_id with the login
name or ID of the user you would like to add as a provisional user.
Once this user is added, your provisional application will be able
to authenticate this user via OAuth. Note that this call only works
for applications that do not yet have full access.

#### DELETE /application/provisional-users/:user_id

Submit this with the DELETE method, and again, replace :user_id with
the login_name or ID of the user you would like to remove as a
provisional user.

Please let me know if you have any questions about these methods or
notice any unexpected behavior.

Deleting user tokens
----------------------

Access tokens created by your application for a user should be revoked as appropriate (eg. user logged out of your app, user wishes to unlink their Etsy account and your app etc.)

#### DELETE /appuser

Making this request will revoke the token that was used to make the request. Using this token in the future will result in a "401 Unauthorized" response.


Testing
----------------------

These calls exist primarily for testing connectivity to the Etsy API.

#### GET /public/ping

Simply returns "pong" if your API is valid and you can successfully
connect to the API.
