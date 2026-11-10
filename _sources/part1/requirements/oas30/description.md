## Basic requirements

APIs conforming to this requirements class are self-documenting using an
[OpenAPI Document](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.3.md#oasDocument).

<!-- requirements-class -->

<!-- requirement: oas30/oas-definition-1 -->

<!-- requirement: oas30/oas-definition-2 -->

Two example OpenAPI documents are included in [Annex B](#sec-B.3).

<!-- requirement: oas30/oas-impl -->

## Complete definition

<!-- requirement: oas30/completeness -->

Note APIs that, for example, are access-controlled (see [Security](#sec-11.4)), support web cache
validation, support CORS, or that use HTTP redirection will make use of additional HTTP status codes
beyond regular codes such as 200 for successful GET requests and 400, 404 or 500 for error situations.
See [Clause 8.2](#sec-8.2).

Clients should be prepared to receive responses not documented in the OpenAPI definition. For example,
additional errors may occur in the transport layer outside of the server.

## Exceptions

<!-- requirement: oas30/exceptions-codes -->

*Example — An exception response object definition* (see also the
[Exception response](bblocks://ogc.api.common.part1.responses.Exception) building block)

```yaml
description: An error occurred.
content:
  application/json:
    schema:
      $ref: http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/schemas/exception.yaml
  text/html:
    schema:
      type: string
```

## Security

OpenAPI uses two constructs to describe the security features of an API; Security Requirements and
Security Schemes. Security Requirements are packaged in an array. Only one of the Security Requirements
in the array must be met in-order to authorize a request. Security Requirements are associated with one
or more Security Schemes. Each Security Scheme describes a security control (ex. HTTP authentication).
All of the security schemes associated with a Security Requirement must be satisfied in order for that
Security Requirement to be met.

Security Requirements can be defined at the following levels.

- Root — applicable to the whole API except when overridden by Security Requirements defined at a lower
  level of the API.
- Operation — only applicable to this operation. Overrides any requirements defined at the Root level.

The OpenAPI specification currently supports the following
[security schemes](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.3.md#security-scheme-object):

- HTTP authentication;
- An API key (either as a header or as a query parameter);
- OAuth2’s common flows (implicit, password, application and access code) as defined in RFC6749; and
- OpenID Connect Discovery.

<!-- requirement: oas30/security -->

## Query Parameter Definition

The OpenAPI specification defines query parameters using the Parameter object with the `in` property set
to “query.” The parameter name is a literal value provided by the `name` property. Since the parameter
names are literals, each parameter must be described separately.

OGC API — Common requires that all query parameters are specified in the API definition. In the case of
a Feature server, this could mean that every property of every feature type must be described in the API
definition, a requirement that few implementers would accept.

The OpenAPI specification provides a capability that allows additional parameters to be specified
without explicitly declaring them. That is, parameters that have not been explicitly specified in the
API definition for the operation will still be considered “specified” for purposes of validation (see
`/per/core/query-param-name-specified` and `/per/core/query-param-name-tolerance`).

```yaml
in: query
name: freeFormParameters
schema:
  type: object
  additionalProperties: true
style: form
```

*Figure 6 — OpenAPI schema for additional "free-form" query parameters*

Note that the name of the parameter does not matter as the actual query parameters are the names of the
object properties. For example, assume that the value of `freeFormParameters` is this object:

```json
{
  "my_first_parameter": "some value",
  "my_other_parameter": 42
}
```

*Figure 7 — Example "free-form" query parameter*

In the request URI this would be expressed as `&my_first_parameter=some%20value&my_other_parameter=42`.

## Further Information

Additional guidance on using OpenAPI in OGC Web API implementations can be found in the
[OGC API — Common — Users Guide](http://www.opengis.net/doc/UG/ogcapi-common/1.0#oas30-usage-section).
