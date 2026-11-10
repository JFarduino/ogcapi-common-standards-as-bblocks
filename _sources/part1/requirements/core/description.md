The following requirements and recommendations define protocol-level conventions that should be
applicable to all OGC Web APIs. The requirements of this class are listed in the
[Requirements](#req-clause-8-requirements) section at the end of this clause; the recommendations and
permissions are given in the subclauses below.

## 8.1 HTTP 1.1

The standards used for Web APIs are built on the HTTP protocol. Therefore, conformance with HTTP or a
closely related protocol is required: see requirement [`/req/core/http`](#req-core-http).

## 8.2 HTTP Status Codes

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

| **Recommendation 2** | `/per/core/additional-status-codes` |
|---|---|
| **A** | Servers MAY implement additional capabilities provided by the HTTP protocol. Therefore, they MAY return status codes in addition to those listed in Table 2. |

When a server encounters an error in the processing of a request, the server may wish to include
information in addition to the status code in the response. Since Web API interactions are often
machine-to-machine, a machine-readable report would be preferred. IETF RFC 7807 addresses this need by
providing “Problem Details” response schemas for both JSON and XML (see the
[Exception schema](bblocks://ogc.api.common.part1.schemas.exception) building block).

| **Recommendation 3** | `/rec/core/problem-details` |
|---|---|
| **A** | An OGC Web API should include a “Problem Details” report in any error response in accordance with IETF RFC 7807. |

## 8.3 Query parameters

### 8.3.1 Parameter Names

See requirement [`/req/core/query-param-name-unknown`](#req-core-query-param-name-unknown).

The criteria for a parameter to be “specified” in the API definition depends on the API definition
language used, the complexity of the resources exposed, and the ability of the API server to tolerate
errors.

A service implementer should endeavor to provide as much detail in the server’s API definition as the
API definition language allows. However, there is no requirement for the API definition to list every
endpoint for which there is a non-404 behavior, for it to list every possible query parameter that might
affect the behavior of an endpoint, or for it to list every possible value that each query parameter
might accept.

| **Recommendation 4** | `/per/core/query-param-name-specified` |
|---|---|
| **A** | The specification of a query parameter in the API definition MAY encompass a range of parameter names. Any query parameter that falls within the specified range can be considered “specified” in the API definition. |
| **Statement** | Examples of a parameter range include:<br>• A regular expression that defines the valid parameter names,<br>• A URI Template segment that defines the valid parameter names,<br>• An indication that all parameter names are accepted (no parameter validation). |

| **Recommendation 5** | `/per/core/query-param-name-tolerance` |
|---|---|
| **A** | Servers MAY display tolerance for requests with incorrect query parameter names. These acts of tolerance include:<br>• Accept alternate capitalizations, spellings, and/or aliases of parameters,<br>• Ignore unknown/unrecognized parameters,<br>• Return a response with a status code of 30x redirecting the client to a more correct version of the request. |
| **B** | Servers should not be excessively tolerant. The response a client receives from the server should be a reasonable response for the request submitted. |

### 8.3.2 Parameter Values

See requirement [`/req/core/query-param-value-invalid`](#req-core-query-param-value-invalid).

The criteria for a parameter value to be considered “invalid” varies with the expressiveness of the API
definition language used and the ability of the API server to tolerate errors.

A service implementer should endeavor to provide as much detail in the server’s API definition as the
API definition language allows. However, there is no requirement to list every possible value that each
query parameter might accept. Rather, the API implementation should include a reasonable degree of error
recovery.

| **Recommendation 6** | `/per/core/query-param-value-specified` |
|---|---|
| **A** | The specification of a query parameter in the API definition should include a definition of the valid values for that parameter. Any value that meets that criteria can be considered “specified” in the API definition. |
| **B** | The API definition language chosen may not be capable of expressing the desired range of values. In that case the server SHOULD provide:<br>• A definition of the parameter values that best expresses the intended use of that parameter,<br>• Additional human readable text documenting the actual range of validity. |

| **Recommendation 7** | `/per/core/query-param-value-tolerance` |
|---|---|
| **A** | Servers MAY display tolerance for requests where a parameter has an incorrect value. These acts of tolerance include:<br>• substituting default values for invalid ones,<br>• correcting formatting errors (e.g. convert integers to float). |
| **B** | Servers should not be excessively tolerant. The response a client receives from the server should be a reasonable response for the request submitted. |

## 8.4 Web Caching

Entity tags are a mechanism for web cache validation and for supporting conditional requests to reduce
network traffic. Entity tags are specified by HTTP 1.1 (RFC 7232).

| **Recommendation 8** | `/rec/core/etag` |
|---|---|
| **A** | The service SHOULD support entity tags and the associated headers as specified by HTTP 1.1. |

## 8.5 Support for Cross-Origin Requests

If the data is located on another host than the webpage (“same-origin policy”), access to data from a
HTML page is by default prohibited for security reasons. A typical example is a web-application
accessing feature data from multiple distributed datasets.

| **Recommendation 9** | `/rec/core/cross-origin` |
|---|---|
| **A** | If the server is intended to be accessed from a browser, cross-origin requests SHOULD be supported. Note that support can also be added in a proxy layer on top of the server. |

Two common mechanisms to support cross-origin requests are:

- [Cross-origin resource sharing (CORS)](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing)
- [JSONP (JSON with padding)](https://en.wikipedia.org/wiki/JSONP)

## 8.6 String Internationalization

If the server supports representing resources in multiple languages, the usual HTTP content negotiation
mechanisms apply. The client states its language preferences in the `Accept-Language` header of a
request and the server responds with responses that have linguistic text in the language that best
matches the requested languages and the capabilities of the server.

| **Recommendation 10** | `/rec/core/string-i18n` |
|---|---|
| **A** | For encodings that support string internationalization, the server SHOULD include information about the language for each string value that includes linguistic text. |

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

## 8.7 Resource Encodings

A Web API provides access to resources through representations of those resources. One property of a
representation is the format used to encode it for transfer. Components negotiate the encoding format to
use through the content negotiation process defined in IETF RFC 7231.

Additional content negotiation techniques are allowed, but support is not required of implementations
conformant to this Standard.

While this Standard does not specify any mandatory encoding, the following encodings are recommended:

HTML encoding recommendation:

| **Recommendation 11** | `/rec/core/html` |
|---|---|
| **A** | To support browsing an API with a web browser and to enable search engines to crawl and index the dataset, implementations SHOULD consider supporting an HTML encoding. |

JSON encoding recommendation:

| **Recommendation 12** | `/rec/core/json` |
|---|---|
| **A** | To support processing of an API with a web applet, implementations SHOULD consider supporting a JSON encoding. |

Requirement [`/req/core/http`](#req-core-http) implies that the encoding of a server response is
determined using content negotiation as specified by the HTTP RFC.

The section [Media Types](#clause-13) includes guidance on media types for encodings that are specified
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

## 8.8 Parameter Encoding

The following sections provide the requirements and guidelines for encoding parameters for use in an
OGC Web API request.

OGC Web API requests are issued using a URI. The URI syntax is defined in IETF RFC 3986. Rules for
building URI Templates can be found in IETF RFC 6570.

The Backus-Naur Form (BNF) definition of a URI is provided in [Annex D.1](#annex-d).

### 8.8.1 Capitalization

IETF RFC 3986 sections 6.2.2.1 and 2.1 provide the requirements for capitalization in URIs: see
requirement [`/req/core/query-param-capitalization`](#req-core-query-param-capitalization).

In order to minimize capitalization issues for implementers of OGC Web API standards:

| **Recommendation 13** | `/rec/core/query-param-capitalization` |
|---|---|
| **A** | Query parameter names SHOULD be in kebab case. |
| **B** | Query parameter values are usually reflective of the internal structure of the target resource. Unless otherwise specified, these values SHOULD be in kebab case. |

A Web API may allow filtering on properties of the target resource. In that case, the parameter name
would be the name of the resource property. These names are defined by the standards and specifications
defining the resource and cannot be constrained by this Standard.

### 8.8.2 Parameter Value Lists

Parameters may pass more than one value. These lists of parameter values may be passed in two ways.

1. Repeated name:value pairs where the parameter name is repeated for each value in the list
2. A parameter name followed by a delimited list of values.

The following requirements define how to encode a delimited list (case 2) of parameter values. They do
not apply if replication (case 1) is used: see requirements
[`/req/core/query-param-list-delimiter`](#req-core-query-param-list-delimiter),
[`/req/core/query-param-list-escape`](#req-core-query-param-list-escape) and
[`/req/core/query-param-list-empty`](#req-core-query-param-list-empty).

Thus, two successive commas indicate an empty item, as does a leading comma or a trailing comma. An
empty list can either be interpreted as a list containing no items or as a list containing a single empty
item, depending on the context.

### 8.8.3 Numeric and Boolean Values

The Geospatial field is a mathematical discipline. A clear and accurate exchange of mathematical values
is essential. The encoding rules in this section standardize the encoding of numeric and Boolean
primitives when included in a URI. These rules are based on the computer science basic data types
identified by Kernighan and Ritchie.

- Boolean values conform to requirement
  [`/req/core/query-param-value-boolean`](#req-core-query-param-value-boolean).
- Integer values conform to requirement
  [`/req/core/query-param-value-integer`](#req-core-query-param-value-integer).
- Real numbers can be represented using either the decimal or double (exponential) format. The decimal
  format is typically used except for very large or small values. Decimal values conform to requirement
  [`/req/core/query-param-value-decimal`](#req-core-query-param-value-decimal), and double values conform
  to requirement [`/req/core/query-param-value-double`](#req-core-query-param-value-double).

Special values, if supported, should conform to the following recommendation.

| **Recommendation 14** | `/rec/core/query-param-value-special` |
|---|---|
| **A** | The special values positive and negative infinity and not-a-number SHOULD be represented using the strings `inf`, `-inf` and `nan`, respectively. |

<!-- requirements -->
