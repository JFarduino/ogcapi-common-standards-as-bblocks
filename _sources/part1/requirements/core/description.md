The following requirements and recommendations define protocol-level conventions that should be
applicable to all OGC Web APIs.

<!-- requirements-class -->

## HTTP 1.1

The standards used for Web APIs are built on the HTTP protocol. Therefore, conformance with HTTP or a
closely related protocol is required.

<!-- requirement: core/http -->

## HTTP Status Codes

Table 2 lists the main HTTP status codes that clients should be prepared to receive. This includes
support for specific security schemes or URI redirection. In addition, other error situations may occur
in the transport layer outside of the server.

*Table 2 — Typical HTTP status codes*

| Status code | Description |
|---|---|
| `200` | A successful request. |
| `302` | The target resource was found but resides temporarily under a different URI. A 302 response is not evidence that the operation has been successfully completed. |
| `303` | The server is redirecting the user agent to a different resource. A 303 response is not evidence that the operation has been successfully completed. |
| `304` | An entity tag was provided in the request and the resource has not changed since the previous request. |
| `307` | The target resource resides temporarily under a different URI and the user agent MUST NOT change the request method if it performs an automatic redirection to that URI. |
| `308` | Indicates that the target resource has been assigned a new permanent URI and any future references to this resource ought to use one of the enclosed URIs. |
| `400` | The server cannot or will not process the request due to an apparent client error. For example, a query parameter had an incorrect value. |
| `401` | The request requires user authentication. The response includes a WWW-Authenticate header field containing a challenge applicable to the requested resource. |
| `403` | The server understood the request, but is refusing to fulfill it. While status code 401 indicates missing or bad authentication, status code 403 indicates that authentication is not the issue, but the client is not authorized to perform the requested operation on the resource. |
| `404` | The requested resource does not exist on the server. For example, a path parameter had an incorrect value. |
| `405` | The request method is not supported. For example, a POST request was submitted, but the resource only supports GET requests. |
| `406` | Content negotiation failed. For example, the Accept header submitted in the request did not support any of the media types supported by the server for the requested resource. |
| `500` | An internal error occurred in the server. |

The return status codes described in Table 2 do not cover all possible conditions. See IETF RFC 7231 for
a complete list of HTTP status codes.

<!-- recommendation: core/additional-status-codes -->

When a server encounters an error in the processing of a request, the server may wish to include
information in addition to the status code in the response. Since Web API interactions are often
machine-to-machine, a machine-readable report would be preferred. IETF RFC 7807 addresses this need by
providing “Problem Details” response schemas for both JSON and XML (see the
[Exception schema](bblocks://ogc.api.common.part1.schemas.exception) building block).

<!-- recommendation: core/problem-details -->

## Query parameters

### Parameter Names

<!-- requirement: core/query-param-name-unknown -->

The criteria for a parameter to be “specified” in the API definition depends on the API definition
language used, the complexity of the resources exposed, and the ability of the API server to tolerate
errors.

A service implementer should endeavor to provide as much detail in the server’s API definition as the
API definition language allows. However, there is no requirement for the API definition to list every
endpoint for which there is a non-404 behavior, for it to list every possible query parameter that might
affect the behavior of an endpoint, or for it to list every possible value that each query parameter
might accept.

<!-- recommendation: core/query-param-name-specified -->

<!-- recommendation: core/query-param-name-tolerance -->

### Parameter Values

<!-- requirement: core/query-param-value-invalid -->

The criteria for a parameter value to be considered “invalid” varies with the expressiveness of the API
definition language used and the ability of the API server to tolerate errors.

A service implementer should endeavor to provide as much detail in the server’s API definition as the
API definition language allows. However, there is no requirement to list every possible value that each
query parameter might accept. Rather, the API implementation should include a reasonable degree of error
recovery.

<!-- recommendation: core/query-param-value-specified -->

<!-- recommendation: core/query-param-value-tolerance -->

## Web Caching

Entity tags are a mechanism for web cache validation and for supporting conditional requests to reduce
network traffic. Entity tags are specified by HTTP 1.1 (RFC 7232).

<!-- recommendation: core/etag -->

## Support for Cross-Origin Requests

If the data is located on another host than the webpage (“same-origin policy”), access to data from a
HTML page is by default prohibited for security reasons. A typical example is a web-application
accessing feature data from multiple distributed datasets.

<!-- recommendation: core/cross-origin -->

Two common mechanisms to support cross-origin requests are:

- [Cross-origin resource sharing (CORS)](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing)
- [JSONP (JSON with padding)](https://en.wikipedia.org/wiki/JSONP)

## String Internationalization

If the server supports representing resources in multiple languages, the usual HTTP content negotiation
mechanisms apply. The client states its language preferences in the `Accept-Language` header of a
request and the server responds with responses that have linguistic text in the language that best
matches the requested languages and the capabilities of the server.

<!-- recommendation: core/string-i18n -->

For example, if JSON-LD is used as an encoding, the built-in capabilities to
[annotate a string with its language](https://www.w3.org/TR/json-ld/#string-internationalization)
should be used.

The [link object](http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/schemas/link.yaml) based on
RFC 8288 (Web Linking) includes a `hreflang` attribute that can be used to state the language of the
referenced resource. This can be used to include links to the same data in, for example, English or
French. Just like with multiple encodings, a server that wants to use language-specific links will have
to support a mechanism to mint language-specific URIs for resources in order to express links to, for
example, the same resource in another language. Again, this document does not mandate any particular
approach how such a capability is supported by the server.

## Resource Encodings

A Web API provides access to resources through representations of those resources. One property of a
representation is the format used to encode it for transfer. Components negotiate the encoding format to
use through the content negotiation process defined in IETF RFC 7231.

Additional content negotiation techniques are allowed, but support is not required of implementations
conformant to this Standard.

While this Standard does not specify any mandatory encoding, the following encodings are recommended:

HTML encoding recommendation:

<!-- recommendation: core/html -->

JSON encoding recommendation:

<!-- recommendation: core/json -->

Requirement [`/req/core/http`](#req-core-http) implies that the encoding of a server response is
determined using content negotiation as specified by the HTTP RFC.

The section [Media Types](#sec-12) includes guidance on media types for encodings that are specified
in this document.

Note that any server that supports multiple encodings will have to support a mechanism to mint
encoding-specific URIs for resources in order to express links, such as, to alternate representations of
the same resource. This Standard does not mandate any particular approach for how this is supported by
the server.

As clients simply need to dereference the URI of the link, the implementation details and the mechanism
of how the encoding is included in the URI of the link are not important. Developers interested in the
approach of a particular implementation, such as manipulating (“hacking”) URIs in the browser address
bar, can study the API Definition document for that server.

Two common approaches are to use:

- An additional path for each encoding of each resource (this can be expressed, for example, using
  format specific suffixes like “.html”);
- An additional query parameter (for example, “accept” or “f”) that overrides the Accept header of the
  HTTP request.

## Parameter Encoding

The following sections provide the requirements and guidelines for encoding parameters for use in an
OGC Web API request.

OGC Web API requests are issued using a URI. The URI syntax is defined in IETF RFC 3986. Rules for
building URI Templates can be found in IETF RFC 6570.

The Backus-Naur Form (BNF) definition of a URI is provided in [Annex D.1](#sec-D.1).

### Capitalization

IETF RFC 3986 sections 6.2.2.1 and 2.1 provide the requirements for capitalization in URIs.

<!-- requirement: core/query-param-capitalization -->

In order to minimize capitalization issues for implementers of OGC Web API standards:

<!-- recommendation: core/query-param-capitalization -->

A Web API may allow filtering on properties of the target resource. In that case, the parameter name
would be the name of the resource property. These names are defined by the standards and specifications
defining the resource and cannot be constrained by this Standard.

### Parameter Value Lists

Parameters may pass more than one value. These lists of parameter values may be passed in two ways.

1. Repeated name:value pairs where the parameter name is repeated for each value in the list
2. A parameter name followed by a delimited list of values.

The following requirements define how to encode a delimited list (case 2) of parameter values. They do
not apply if replication (case 1) is used.

<!-- requirement: core/query-param-list-delimiter -->

<!-- requirement: core/query-param-list-escape -->

<!-- requirement: core/query-param-list-empty -->

Thus, two successive commas indicate an empty item, as does a leading comma or a trailing comma. An
empty list can either be interpreted as a list containing no items or as a list containing a single empty
item, depending on the context.

### Numeric and Boolean Values

The Geospatial field is a mathematical discipline. A clear and accurate exchange of mathematical values
is essential. The encoding rules in this section standardize the encoding of numeric and Boolean
primitives when included in a URI. These rules are based on the computer science basic data types
identified by Kernighan and Ritchie.

Boolean values conform to the following requirement.

<!-- requirement: core/query-param-value-boolean -->

Integer values conform to the following requirement.

<!-- requirement: core/query-param-value-integer -->

Real numbers can be represented using either the decimal or double (exponential) format. The decimal
format is typically used except for very large or small values.

Decimal values conform to the following requirement.

<!-- requirement: core/query-param-value-decimal -->

Double values conform to the following requirement.

<!-- requirement: core/query-param-value-double -->

Special values, if supported, should conform to the following recommendation.

<!-- recommendation: core/query-param-value-special -->
