API Gateway
===========

This is a microservice that sits in front of most SMARTA srevices, although it can also be accessed independently at `api-gateway.services.smartatransit.com` for debugging purposes. It serves to validate and parse SMARTA API authorization and pass it on to the internal server. It behaves as follows:

1. When a request is received, the `Authorization` header is checked. If it is missing, a 401 is returned.
2. If the header begins with `Key `, the remainder of the header is parsed as `<client_id>|<client_secret>`. These values are then used to obtain a JWT for the server from Auth0. The resulting tokens are stored in an in-memory cache, keyed by the entire API key `<client_id>|<client_secret>`, and marked with their expiration moment. Expired tokens are cleared out on a regular basis to avoid memory bloat over time.
3. Otherwise, if the header begins with `Bearer `, the remainder of the header is taken to be a JWT value.
4. In either case 2 or 3, the resulting token is parsed, the signature is validated, and the values in the token are used to populate response headers `X-Smarta-Auth-Role` and `X-Smarta-Auth-Session`. In the event that the service is acting as a gateway to another service, these headers will not actually be returned to the caller, they will be forwarded to the requested service.

The service ignores the request path, method, and body and does not return any body. When acting as a gateway, the path, method, and body are all forwarded directly to the relevant service if the request is deemed authorized.
