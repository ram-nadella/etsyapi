The Etsy API Reference
=========================

Listings
----------------------

#### POST /shop/:shop_id/listings/:listing_id/renewals

**OAuth Scope:** listings_w

Renews the listing with the given listing ID.

Provisional Users
----------------------

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
