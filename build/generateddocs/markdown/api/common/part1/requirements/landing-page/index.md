
# Landing Page Requirements Class (Requirements-class)

`ogc.api.common.part1.requirements.landing-page` *v1.0.0*

Requirements class "Landing Page": the landing page, the API definition and the conformance declaration resources of an OGC Web API.

[*Status*](http://www.opengis.net/def/status): Stable

## Description

<!-- requirements-class -->

The Landing Page Requirements Class of the OGC API — Common — Part 1: Core Standard describes how the
Landing Page and its associated resources are accessed through an OGC conformant Web API.

The Landing Page resources are introduced in Table 3. The requirements and recommendations applicable
to these resources are provided in the sections below.

*Table 3 — Landing Page Resources*

| Resource | HTTP Method | Description |
|---|---|---|
| Landing Page | GET | the landing page |
| API Definition | GET | the API Definition document for this API |
| Conformance Declaration | GET | the conformance information for this API |

## API landing page

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
[example landing page](#sec-B.1) for an example of the use of markup in the attribution element.

### Operation

<!-- requirement: landing-page/root-op -->

### Response

<!-- requirement: landing-page/root-success -->

The Landing Page returned by this operation is based on the following OpenAPI schema.

```yaml include=https://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/schemas/landingPage.yaml bblock=ogc.api.common.part1.schemas.landingPage
```

*Figure 4 — Landing Page Schema*

In addition to the required resources, links to additional resources may be included in the Landing
Page.

Examples of OGC API landing pages are provided in [Annex B.1](#sec-B.1).

A JSON schema for the Landing Page resource can be found on the
[OGC Schema Repository](http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/schemas/landingPage.yaml).

### Error Situations

See [Clause 8.2](#sec-8.2) for general guidance.

## API Definition

Every API implementation should provide an API Definition resource that describes the capabilities
provided by that API. This resource can be used by client developers to understand the supported
services, by software clients to connect to the server, and by development tools to support the
implementation of servers and clients.

### Operation

<!-- requirement: landing-page/api-definition-op -->

<!-- recommendation: landing-page/api-definition-op -->

### Response

<!-- requirement: landing-page/api-definition-success -->

> **NOTE** The -f parameter MAY be used to satisfy this requirement.

<!-- recommendation: landing-page/api-definition-oas -->

### Error Situations

See [Clause 8.2](#sec-8.2) for general guidance.

## Declaration of Conformance Classes

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

### Operation

<!-- requirement: landing-page/conformance-op -->

### Response

<!-- requirement: landing-page/conformance-success -->

The Conformance Declaration returned by this operation is based on the following OpenAPI schema.

```yaml include=bblocks://ogc.api.common.part1.schemas.confClasses
```

*Figure 5 — Conformance Declaration Schema*

A JSON schema for the Landing Page resource can be found on the
[OGC Schema Repository](http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/schemas/confClasses.yaml).

Examples of OGC Conformance Declarations are provided in [Annex B.2](#sec-B.2).

### Error situations

See [Clause 8.2](#sec-8.2) for general guidance.

## Sources

* [OGC 19-072 — OGC API - Common - Part 1: Core — Landing Page Requirements Class](https://docs.ogc.org/is/19-072/19-072.html#rc_landing-page-section)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-common-standards-as-bblocks](https://github.com/JFarduino/ogcapi-common-standards-as-bblocks)
* Path: `_sources/part1/requirements/landing-page`

