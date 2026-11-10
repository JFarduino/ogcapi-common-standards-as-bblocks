
# Conventions (Clause)

`ogc.api.common.part1.clauses.conventions` *v1.0.0*

Clause 6 of OGC API - Common - Part 1: Core: Web API fundamentals, identifiers, links, link relations, use of HTTPS and API definitions.

[*Status*](http://www.opengis.net/def/status): Stable

## Description

## Web API Fundamentals

The following concepts are critical to understanding OGC Web API Standards.

- The purpose of a Web API is to provide a uniform interface to resources.
- Resources are uniquely identified using Uniform Resource Identifiers (URI).
- A user manipulates a resource through representations of that resource.
- A representation is the current or intended state of a resource encoded for exchange between
  components.
- The format used to encode a representation is negotiated between the components participating in the
  exchange.
- Representations are exchanged between components using the HTTP protocol and the operations (GET,
  PUT, etc.) that HTTP supports.

## Identifiers

The Architecture of the World Wide Web establishes the URI as the single global identification system
for the Web. Therefore, URIs or URI Templates are used in OGC Web API Standards to identify key entities
in those Standards.

In accordance with OGC policy, only the Uniform Resource Locator (URL) form of URIs is used.

The normative provisions in this Standard are denoted by the URI
`http://www.opengis.net/spec/ogcapi-common-1/1.0`. All Requirements, Requirements Modules and
Conformance Modules that appear in this document are denoted by partial URIs that are relative to this
base.

Resources described in this document are denoted by partial URIs that are relative to the root node of
the API. This node serves as the head of the resource tree exposed through an API. In OpenAPI, the root
node is identified by the `url` field of the
[Server Object](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.3.md#server-object).
In this document the tag `{root}` designates the root node of a URI.

The partial URIs used to identify Resources in this document are referred to as the resource path. The
purpose of a resource path is to identify the referenced resource within the context of this Standard.
Implementers are encouraged to use these partial URIs in their implementations, thereby providing a
common look and feel to OGC APIs.

The OGC API — Common — Part 1 Standard defines Resources, which may appear in more than one place in the
API. These Resource Types are identified by name rather than by URI.

**Summary for Developers:**

RFC 3986 defines a URI in Backus-Naur Form (BNF) as follows:

```text
URI = scheme ":" hier-part [ "?" query ] [ "#" fragment ]

        hier-part     = "//" authority path-abempty
                         / path-absolute
                         / path-rootless
                         / path-empty

        authority     = [ userinfo "@" ] host [ ":" port ]

        path-abempty  = *( "/" segment )

        path-absolute = "/" [ segment-nz *( "/" segment ) ]

        path-rootless = segment-nz *( "/" segment )

        path-empty    = 0<pchar>
```

*Figure 1 — Backus-Naur Definition of URI*

The following rules should be used when interpreting the BNF for use with this Standard:

- scheme is assumed to be HTTP or HTTPS;
- authority is provided by the API developer;
- `{root}` designates the scheme, authority, and path to the root node of the API implementation;
- Only the path-absolute and path-rootless patterns are used;
- Parameters passed as part of an operation are encoded in the query; and
- Parameters passed in HTTP headers or as cookies are out of scope for this Standard.

The following example shows a URI categorized according to RFC 3986 and OGC Web API Standards.

```text
URI     https://example.com:8042/myapi/mydata/?name=roads#centerline
        \____/ \_______________/ \__________/ \_________/ \________/
          |           |               |            |           |
3986    scheme     authority         path         query      fragment
        \______________________/ \__________/ \____________________/
                      |               |                 |
OGC                {root}            path            parameters
```

*Figure 2 — Example URI and Components*

This document does not restrict the lexical space of URIs used in the API beyond the requirements of the
HTTP and URI Syntax IETF RFCs. If URIs include reserved characters that are delimiters in the URI
subcomponent, these have to be percent-encoded. See Clause 2 of RFC 3986 for details.

> **NOTE** OGC Web API Standards may include a community-defined identifier as part of a URI (for
> example: image id or feature id). Definition of the format of those identifiers is out of scope for
> these Standards. Implementers should take care that these identifiers are properly encoded (see RFC
> 3986) in the URIs for all hosted resources.

Additional information on this topic is provided in the
[OGC API — Common — Users Guide](http://www.opengis.net/doc/UG/ogcapi-common/1.0#identifiers-section).

## Links

OGC Web API Standards use RFC 8288 (Web Linking) to express relationships between resources. Resource
representations defined in these Standards commonly include a “links” element. A “links” element is an
array of individual hyperlink elements. These “links” elements provide a convention for associating
related resources.

The individual hyperlink elements that make up a “links” element are defined using the following
[Hyperlink Schema](http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/schemas/link.yaml).

```yaml include=bblocks://ogc.api.common.part1.schemas.link
```

*Figure 3 — Link Relation Schema*

> **NOTE** The `href` value is not restricted to absolute links. Relative links are also allowed.

In addition, links should be passed in the response using HTTP link headers. These links are accessible
to the client without a need to process the resource.

<!-- recommendation: core/link-header -->

Additional information on this topic is provided in the
[OGC API — Common — Users Guide](http://www.opengis.net/doc/UG/ogcapi-common/1.0#link-relations-section).

## Link relations

Link relation types identify the semantics of a link. For example, a link with the relation type
“service-meta” indicates that the current link context has service metadata at the link target.

Link relation types are expressed using the “rel” property from the Hyperlink Schema.

The “rel” property is populated using values from the
[IANA Link Relations Registry](https://www.iana.org/assignments/link-relations/link-relations.xhtml)
wherever possible. Additional values are registered with the
[OGC Link Relation Registry](http://www.opengis.net/def/rel). Additional relation type values can be
used if neither of these registers suffice.

The link relationships used in the OGC API — Common — Part 1: Core Standard are described in Table 1.
Additional relation types may be used if the implementation warrants it.

*Table 1 — Link Relations*

| Link Relation | Purpose |
|---|---|
| `alternate` | Refers to a substitute for this context [IANA]. Refers to a representation of the current resource that is encoded using another media type (the media type is specified in the type link attribute). |
| `http://www.opengis.net/def/rel/ogc/1.0/data-meta` | Identifies general metadata for the context (dataset or collection) that is primarily intended for consumption by machines. |
| `http://www.opengis.net/def/rel/ogc/1.0/conformance` | Refers to a resource that identifies the specifications that the link’s context conforms to. [OGC] |
| `describedby` | Refers to a resource providing information about the link’s context. [IANA] Links to external resources that further describe the subject resource |
| `license` | Refers to a license associated with this context. [IANA] |
| `self` | Conveys an identifier for the link’s context. [IANA] A link to another representation of this resource. |
| `service-desc` | Identifies service description for the context that is primarily intended for consumption by machines. [IANA] API definitions are considered service descriptions. |
| `service-doc` | Identifies service documentation for the context that is primarily intended for human consumption. [IANA] |
| `service-meta` | Identifies general metadata for the context that is primarily intended for consumption by machines. [IANA] |

Additional information on the use of link relationships is provided in the
[OGC API — Common — Users Guide](http://www.opengis.net/doc/UG/ogcapi-common/1.0#link-relations-section).

## Use of HTTPS

For simplicity, this OGC Standard only refers to the HTTP protocol. This is not meant to exclude the use
of HTTPS. This is simply a shorthand notation for “HTTP or HTTPS”. In fact, most servers are expected to
use HTTPS and not HTTP.

OGC Web API Standards do not prohibit the use of any valid HTTP option. However, implementers should be
aware that optional capabilities that are not in common use could be an impediment to interoperability.

## API definition

### General remarks

This OGC Standard specifies requirements and recommendations for the development of APIs that share
spatial resources while using a Standard way of doing so. In general, APIs will go beyond the
requirements and recommendations stated in this Standard. They will support additional operations,
parameters, and so on, that are specific to the API or the software tool used to implement the API.

So that client developers can more easily learn how to use the API, good documentation is essential. In
the best case, documentation would be available both in HTML for human consumption and in a
machine-readable format that can be processed by software for run-time binding. The use of OpenAPI is
one way to provide that machine-readable documentation.

### Role of OpenAPI

This OGC API Standard uses OpenAPI 3.0 fragments in examples and to formally state requirements. Using
OpenAPI 3.0 is not required for implementing an OGC API. Other API definition languages may be used
along with, or instead of, OpenAPI. However, any API definition language used should have an associated
conformance class advertised through the `/conformance` path.

This Standard includes a conformance class for OGC API definitions that follow the OpenAPI specification
3.0. Alternative API definition languages are also allowed. Conformance classes for additional API
definition languages will be added as the OGC API landscape continues to evolve.

### References to OpenAPI components in normative statements

Some normative statements (requirements, recommendations and permissions) use a phrase that a component
in the API definition of the server must be “based upon” a schema or parameter component in the OGC
schema repository.

In this case, the following changes to the pre-defined OpenAPI component are permitted.

- If the server supports an XML encoding, `xml` properties may be added to the relevant OpenAPI schema
  components.
- The range of values of a parameter or property may be extended (additional values) or constrained (if
  a subset of all possible values is applicable to the server). An example for a constrained range of
  values is to explicitly specify the supported values of a string parameter or property using an enum.
- Additional properties may be added to the schema definition of a Response Object.
- Informative text may be changed or added, like comments or description properties.

For OGC API definitions that do not conform to the OpenAPI Specification 3.0, the normative statement
should be interpreted in the context of the API definition language used.

### Reusable OpenAPI components

Reusable components for OpenAPI definitions for an OGC API are referenced from this document. They are
available from the OGC Schemas Registry at
[http://schemas.opengis.net/ogcapi/common/part1/1.0](http://schemas.opengis.net/ogcapi/common/part1/1.0)
and as building blocks in the
[OGC API — Common Building Blocks register](https://ogcincubator.github.io/bblocks-ogcapi-common/).

Additional information on the use of OpenAPI as an API definition is provided in the
[OGC API — Common — Users Guide](http://www.opengis.net/doc/UG/ogcapi-common/1.0#oas30-usage-section).

## Sources

* [OGC 19-072 — OGC API - Common - Part 1: Core — Conventions](https://docs.ogc.org/is/19-072/19-072.html#_conventions)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-common-standards-as-bblocks](https://github.com/JFarduino/ogcapi-common-standards-as-bblocks)
* Path: `_sources/part1/clauses/conventions`

