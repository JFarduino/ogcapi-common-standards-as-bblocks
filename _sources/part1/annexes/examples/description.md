## B.1 Example Landing Pages

*Example — JSON Landing Page*

This example Landing Page response in JSON is for an implementation of the OGC API-Common Standard that
supports:

- HTML
- JSON
- OGC API — Common — Part 2: Geospatial Data

This example also illustrates the self and alternate association types.

```json
{
    "title": "Example API Landing Page",
    "description": "This is an example of an API landing page in JSON format",
    "attribution": "<a href='www.ign.es' rel=' '>IGN</a> <a href='www.govdata.de/dl-de/by-2-0'>(c)</a>",
    "links": [
        {
            "rel": "service-desc",
            "type": "application/json",
            "title": "API definition for this endpoint as JSON",
            "href": "http://www.example.com/oapi-c/api?f=application/json"
        },
        {
            "rel": "service-desc",
            "type": "text/html",
            "title": "API definition for this endpoint as HTML",
            "href": "http://www.example.com/oapi-c/api?f=text/html"
        },
        {
            "rel": "http://www.opengis.net/def/rel/ogc/1.0/data-meta",
            "type": "application/xml",
            "title": "ISO 19115 Metadata as XML",
            "href": "http://www.example.com/oapi-c/data-meta?f=application/xml"
        },
        {
            "rel": "http://www.opengis.net/def/rel/ogc/1.0/conformance",
            "type": "application/json",
            "title": "Conformance Declaration as JSON",
            "href": "http://www.example.com/oapi-c/conformance?f=application/json"
        },
        {
            "rel": "http://www.opengis.net/def/rel/ogc/1.0/conformance",
            "type": "application/xml",
            "title": "Conformance Declaration as XML",
            "href": "http://www.example.com/oapi-c/conformance?f=application/xml"
        },
        {
            "rel": "http://www.opengis.net/def/rel/ogc/1.0/conformance",
            "type": "text/html",
            "title": "Conformance Declaration as HTML",
            "href": "http://www.example.com/oapi-c/conformance?f=text/html"
        },
        {
            "rel": "http://www.opengis.net/def/rel/ogc/1.0/data",
            "type": "application/json",
            "title": "Collections Metadata as JSON",
            "href": "http://www.example.com/oapi-c/collections?f=application/json"
        },
        {
            "rel": "http://www.opengis.net/def/rel/ogc/1.0/data",
            "type": "application/xml",
            "title": "Collections Metadata as XML",
            "href": "http://www.example.com/oapi-c/collections?f=application/xml"
        },
        {
            "rel": "http://www.opengis.net/def/rel/ogc/1.0/data",
            "type": "text/html",
            "title": "Collections Metadata as HTML",
            "href": "http://www.example.com/oapi-c/collections?f=text/html"
        },
        {
            "rel": "self",
            "type": "application/json",
            "title": "This Document",
            "href": "http://www.example.com/oapi-c?f=application/json"
        },
        {
            "rel": "alternate",
            "type": "application/xml",
            "title": "This Document as XML",
            "href": "http://www.example.com/oapi-c?f=application/xml"
        },
        {
            "rel": "alternate",
            "type": "text/html",
            "title": "This Document as HTML",
            "href": "http://www.example.com/oapi-c?f=text/html"
        }
    ]
}
```

The example is presented below in YAML.

```yaml
title: Example API Landing Page
description: This is an example of an API landing page in JSON format
attribution: "<a href='www.ign.es' rel=' '>IGN</a> <a href='www.govdata.de/dl-de/by-2-0'>(c)</a>"
links:
- rel: service-desc
  type: application/json
  title: API definition for this endpoint as JSON
  href: http://www.example.com/oapi-c/api?f=application/json
- rel: service-desc
  type: text/html
  title: API definition for this endpoint as HTML
  href: http://www.example.com/oapi-c/api?f=text/html
- rel: http://www.opengis.net/def/rel/ogc/1.0/data-meta
  type: application/xml
  title: ISO 19115 Metadata as XML
  href: http://www.example.com/oapi-c/data-meta?f=application/xml
- rel: http://www.opengis.net/def/rel/ogc/1.0/conformance
  type: application/json
  title: Conformance Declaration as JSON
  href: http://www.example.com/oapi-c/conformance?f=application/json
- rel: http://www.opengis.net/def/rel/ogc/1.0/conformance
  type: application/xml
  title: Conformance Declaration as XML
  href: http://www.example.com/oapi-c/conformance?f=application/xml
- rel: http://www.opengis.net/def/rel/ogc/1.0/conformance
  type: text/html
  title: Conformance Declaration as HTML
  href: http://www.example.com/oapi-c/conformance?f=text/html
- rel: http://www.opengis.net/def/rel/ogc/1.0/data
  type: application/json
  title: Collections Metadata as JSON
  href: http://www.example.com/oapi-c/collections?f=application/json
- rel: http://www.opengis.net/def/rel/ogc/1.0/data
  type: application/xml
  title: Collections Metadata as XML
  href: http://www.example.com/oapi-c/collections?f=application/xml
- rel: http://www.opengis.net/def/rel/ogc/1.0/data
  type: text/html
  title: Collections Metadata as HTML
  href: http://www.example.com/oapi-c/collections?f=text/html
- rel: self
  type: application/json
  title: This Document
  href: http://www.example.com/oapi-c?f=application/json
- rel: alternate
  type: application/xml
  title: This Document as XML
  href: http://www.example.com/oapi-c?f=application/xml
- rel: alternate
  type: text/html
  title: This Document as HTML
  href: http://www.example.com/oapi-c?f=text/html
```

## B.2 Conformance Examples

*Example — Conformance Response*

This example response in JSON is for an implementation of the OGC API-Common Standard that supports
OpenAPI 3.0 for the API definition, as well as HTML and JSON as encodings for resources.

```json
{
  "conformsTo": [
    "http://www.opengis.net/spec/ogcapi-common-1/1.0/req/core",
    "http://www.opengis.net/spec/ogcapi-common-1/1.0/req/landing-page",
    "http://www.opengis.net/spec/ogcapi-common-1/1.0/req/oas30",
    "http://www.opengis.net/spec/ogcapi-common-1/1.0/req/html",
    "http://www.opengis.net/spec/ogcapi-common-1/1.0/req/json"
  ]
}
```

The example is presented below in YAML.

```yaml
conformsTo:
- http://www.opengis.net/spec/ogcapi-common-1/1.0/req/core
- http://www.opengis.net/spec/ogcapi-common-1/1.0/req/landing-page
- http://www.opengis.net/spec/ogcapi-common-1/1.0/req/oas30
- http://www.opengis.net/spec/ogcapi-common-1/1.0/req/html
- http://www.opengis.net/spec/ogcapi-common-1/1.0/req/json
```

## B.3 API Definition Examples

*Example — JSON API Definition*

This is an example of an API Definition response in JSON (YAML). It describes an implementation of the
OGC API — Common — Part 1: Core Standard.

This example also illustrates:

- Extended metadata (x-keywords),
- Multiple Servers,
- The use of tags to associate external documentation,
- Responses that reference the appropriate JSON schema

```yaml
openapi: 3.0.2
info:
  title: >-
    A sample API conforming to the draft standard OGC API - Common - Part 1:
    Core
  version: 1.0.0
  description: >-
    'This is a sample OpenAPI definition of the draft standard OGC API - Common - Part 1: Core.'
  contact:
    name: Acme Corporation
    email: info@example.org
    url: http://example.org/
  license:
    name: CC-BY 4.0 license
    url: https://creativecommons.org/licenses/by/4.0/
  x-keywords:
    - geospatial
    - data
    - api
servers:
  - url: https://data.example.org/
    description: Production server
  - url: https://dev.example.org/
    description: Development server
tags:
  - name: Capabilities
    description: essential characteristics of this API
  - name: server
    description: Information about the server hosting this API
    externalDocs:
      description: information
      url: https://example.com/sample_api/documentation
paths:
  /:
    get:
      description: >-
        The landing page provides links to the API definition and the
        conformance statements for this API.
      parameters:
        - $ref: '#/components/parameters/f'
      operationId: getLandingPage
      responses:
        '200':
          $ref: 'https://raw.githubusercontent.com/opengeospatial/ogcapi-common/master/core/openapi/3.0/API-Common-Part-1_1_0.yaml#/components/responses/LandingPage'
        '400':
          $ref: '#/components/responses/400'
        '500':
          $ref: '#/components/responses/500'
      summary: Landing page
      tags:
        - server
  /api:
    get:
      description: This document
      parameters:
        - $ref: '#/components/parameters/f'
      responses:
        '200':
          $ref: '#/components/responses/200'
        '400':
          $ref: '#/components/responses/400'
        default:
          $ref: '#/components/responses/400'
      summary: This document
      tags:
        - server
  /conformance:
    get:
      description: >-
        A list of all conformance classes specified in a standard that the
        server conforms to.
      parameters:
        - $ref: '#/components/parameters/f'
      operationId: getConformanceDeclaration
      responses:
        '200':
          $ref: 'https://raw.githubusercontent.com/opengeospatial/ogcapi-common/master/core/openapi/3.0/API-Common-Part-1_1_0.yaml#/components/responses/ConfClasses'
        '400':
          $ref: '#/components/responses/400'
        '500':
          $ref: '#/components/responses/500'
      summary: API conformance definition
      tags:
        - server
components:
  parameters:
    f:
      description: >-
        The optional f parameter indicates the output format that the server
        shall provide as part of the response document.  The default format is JSON.
      explode: false
      in: query
      name: f
      required: false
      schema:
        default: json
        enum:
          - json
          - html
        type: string
      style: form
  responses:
    '200':
      description: successful operation
    '400':
      $ref: 'https://raw.githubusercontent.com/opengeospatial/ogcapi-common/master/core/openapi/3.0/API-Common-Part-1_1_0.yaml#/components/responses/400'
    '500':
      $ref: 'https://raw.githubusercontent.com/opengeospatial/ogcapi-common/master/core/openapi/3.0/API-Common-Part-1_1_0.yaml#/components/responses/500'
```

## B.4 Service Metadata Examples

*Example — Service Metadata*

This is an example of how to extend the OpenAPI info object to include identifying metadata about both
the service and the service provider.

```yaml
info:
  title: My Web API
  version: 1.0.0
  description: This example shows population of an OpenAPI Info element with identifying
    metadata for both the service and the service provider.
  contact:
    name: Acme Corporation
    email: info@example.org
    url: http://example.org/
    x-OGC-serviceContact:
      individualName: John Smith
      positionName: System Administrator
      role: pointOfcontact
      hoursOfService: 24 Hours
      contractInstructions: None
      onlineResource: http://example.org/contact
      address:
        deliveryPoint: 123 Any Street
        city: Boston
        administrativeArea: MA
        postalCode: '12345'
        country: USA
        electronicMailAddress: smith.j@example.org
      telephone:
        voice: "+1.123.456.7890"
        facsimile: "+1.123.456.7890 "
  license:
    name: CC-BY 4.0 license
    url: https://creativecommons.org/licenses/by/4.0/
  x-serviceType: http://www.opengis.net/doc/IS/ogcapi-common-1/1.0
  x-serviceTypeVersion: '1.0'
  x-profile: DGIWG
  x-keywords:
  - geospatial
  - data
  - api
  x-fees: None
  x-accessConstraints: None
```
