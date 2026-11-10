The Landing Page Requirements Class of the OGC API — Common — Part 1: Core Standard describes how the
Landing Page and its associated resources are accessed through an OGC conformant Web API.

The Landing Page resources are introduced in Table 3. The requirements and recommendations applicable
to these resources are provided in the sections below; the requirements of this class are listed in the
[Requirements](#req-clause-9-requirements) section at the end of this clause.

*Table 3 — Landing Page Resources*

| Resource | HTTP Method | Description |
|---|---|---|
| Landing Page | GET | the landing page |
| API Definition | GET | the API Definition document for this API |
| Conformance Declaration | GET | the conformance information for this API |

## 9.1 API landing page

An OGC Web API has a single landing page on the `{root}` node.

The purpose of the landing page is to provide clients with a starting point for using the API. Any
resource exposed through an API can be accessed by following paths or links starting from the landing
page.

The landing page includes three metadata elements: title, description, and attribution. These three
elements describe the API as a whole. Clients can expect to encounter metadata that is more
resource-specific as they follow links and paths from the landing page.

While the three metadata elements are defined as text strings, the attribution element is special.
Specifically, the attribution element can contain markup text. Markup allows a text string to import
images and format text. The capabilities are only limited by the markup language used. See the
[example landing page](#annex-b) for an example of the use of markup in the attribution element.

### 9.1.1 Operation

See requirement [`/req/landing-page/root-op`](#req-landing-page-root-op).

### 9.1.2 Response

See requirement [`/req/landing-page/root-success`](#req-landing-page-root-success).

The Landing Page returned by this operation is based on the following OpenAPI schema (published as the
[Landing Page schema](bblocks://ogc.api.common.part1.schemas.landingPage) building block).

```yaml
type: object
required:
  - links
properties:
  title:
    type: string
    title: The title of the API.
    description: While a title is not required, implementers are strongly advised to include one.
    example: Buildings in Bonn
  description:
    type: string
    example: Access to data about buildings in the city of Bonn via a Web API that conforms to the OGC API Common specification.
  attribution:
    type: string
    title: attribution for the API
    description: The `attribution` should be short and intended for presentation to a user, for example, in a corner of a map. Parts of the text can be links to other resources if additional information is needed. The string can include HTML markup.
  links:
    type: array
    items:
      $ref: link.yaml
```

*Figure 4 — Landing Page Schema*

In addition to the required resources, links to additional resources may be included in the Landing
Page.

Examples of OGC API landing pages are provided in [Annex B.1](#annex-b).

A JSON schema for the Landing Page resource can be found on the
[OGC Schema Repository](http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/schemas/landingPage.yaml).

### 9.1.3 Error Situations

See [Clause 8.2](#8-2-http-status-codes) for general guidance.

## 9.2 API Definition

Every API implementation should provide an API Definition resource that describes the capabilities
provided by that API. This resource can be used by client developers to understand the supported
services, by software clients to connect to the server, and by development tools to support the
implementation of servers and clients.

### 9.2.1 Operation

See requirement [`/req/landing-page/api-definition-op`](#req-landing-page-api-definition-op).

| **Recommendation 15** | `/rec/landing-page/api-definition-op` |
|---|---|
| **A** | The server SHOULD support the HTTP GET operation on the URI `{root}/api`. |
| **B** | The response to the HTTP GET request issued in A SHOULD satisfy requirement `/req/landing-page/api-definition-success`. |

### 9.2.2 Response

See requirement [`/req/landing-page/api-definition-success`](#req-landing-page-api-definition-success).

| **Recommendation 16** | `/rec/landing-page/api-definition-oas` |
|---|---|
| **A** | If the API definition document uses the OpenAPI Specification 3.0, THEN the document SHOULD conform to the [OpenAPI Specification 3.0 requirements class](#clause-12). |

### 9.2.3 Error Situations

See [Clause 8.2](#8-2-http-status-codes) for general guidance.

## 9.3 Declaration of Conformance Classes

The OGC Web API Standards define a collection of modules that can be assembled into a Web API. The first
question a client will ask when accessing one of these APIs is “what are you?” In other words, what
modules were used to create you? Since implementers have a choice on the modules to use, there is no
simple answer. The best that can be done is to provide a list of the modules implemented, a declaration
of the Conformance Classes.

The list of Conformance Classes is key to understanding and using an OGC Web API. So it is important that
they are easy to access. A simple GET using an easily constructed URI is all that should be required.
Therefore, the path to the Conformance Declaration is fixed.

Ease of access is also supported by the structure of the Conformance Declaration resource. It is a simple
list of URIs. This is a structure that requires almost no parsing and little interpretation and is
designed to be accessible to even the simplest client.

### 9.3.1 Operation

See requirement [`/req/landing-page/conformance-op`](#req-landing-page-conformance-op).

### 9.3.2 Response

See requirement [`/req/landing-page/conformance-success`](#req-landing-page-conformance-success).

The Conformance Declaration returned by this operation is based on the following OpenAPI schema
(published as the [Conformance Classes schema](bblocks://ogc.api.common.part1.schemas.confClasses)
building block).

```yaml
type: object
required:
  - conformsTo
properties:
  conformsTo:
    type: array
    items:
      type: string
      example: "http://www.opengis.net/spec/ogcapi-common-1/1.0/conf/core"
```

*Figure 5 — Conformance Declaration Schema*

A JSON schema for the Landing Page resource can be found on the
[OGC Schema Repository](http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/schemas/confClasses.yaml).

Examples of OGC Conformance Declarations are provided in [Annex B.2](#annex-b).

### 9.3.3 Error situations

See [Clause 8.2](#8-2-http-status-codes) for general guidance.

<!-- requirements -->
