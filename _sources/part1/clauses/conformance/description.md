Conformance with this Standard shall be checked using the tests specified in [Annex A](#annex-a)
(normative) of this document. The framework, concepts, and methodology for testing, and the criteria to
claim conformance are specified in the OGC Compliance Testing Policies and Procedures and the
[OGC Compliance Testing web site](https://cite.opengeospatial.org/teamengine/). This Standard addresses
one Standardization Target: [Web APIs](#terms).

OGC API — Common — Part 1: Core provides a common foundation for OGC Web API Standards. The assumption
is that this Standard will only be implemented through inclusion in other Standards. Therefore, all the
relevant abstract tests in Annex A should be included in or referenced by the Abstract Test Suite (ATS)
in each Standard that implements conformance classes defined in this Standard.

This Standard identifies five conformance classes. The conformance classes implemented by an OGC API
are advertised through the `/conformance` resource on the implementation instance of the API’s landing
page. Each conformance class is defined by one requirements class. The tests in Annex A are organized by
Requirements Class. So, an implementation of the Core conformance class must pass all tests specified in
Annex A for the Core requirements class.

| Conformance class | URI | Requirements class |
|---|---|---|
| Core | `http://www.opengis.net/spec/ogcapi-common-1/1.0/conf/core` | [Clause 8](#clause-8) |
| Landing Page | `http://www.opengis.net/spec/ogcapi-common-1/1.0/conf/landing-page` | [Clause 9](#clause-9) |
| HTML | `http://www.opengis.net/spec/ogcapi-common-1/1.0/conf/html` | [Clause 10](#clause-10) |
| JSON | `http://www.opengis.net/spec/ogcapi-common-1/1.0/conf/json` | [Clause 11](#clause-11) |
| OpenAPI 3.0 | `http://www.opengis.net/spec/ogcapi-common-1/1.0/conf/oas30` | [Clause 12](#clause-12) |

The Abstract Test Suite reflects the nature of OGC Web APIs: they are not Web Services in the
traditional sense. Rather, they define the behavior and content of a set of Resources exposed through a
Web Application Programming Interface (Web API). Therefore, an API may expose resources in addition to
those defined by the standard. A test engine must be able to traverse the API, identify and validate
test points, and ignore resource paths that are not to be tested.

## 2.1 Core Requirements Class

The requirements specified in the Core Requirements Class are applicable to all OGC API Standards. They
assure consistent use of the HTTP protocols, provide rules for the construction of URIs, and define
requirements governing the use and processing of URI query parameters. Through these requirements,
OGC API — Common seeks to assure that implementations of OGC API Standards will provide a predictable
interface for their peers.

The Core requirements class is specified in [Clause 8 Core Requirements Class](#clause-8).

## 2.2 Landing Page Requirements Class

The requirements specified in the Landing Page Requirements Class provide a minimal useful service
interface for an OGC Web API. These resources convey a basic understanding of the API and provide a
starting point for further discovery. The requirements specified in this requirements class are
recommended for all OGC Web APIs.

The Landing Page requirements class is specified in [Clause 9 Landing Page Requirements Class](#clause-9).

## 2.3 Encoding Requirements Classes

The OGC API — Common Standard does not mandate a specific encoding or format for representations of
resources. However, both HTML and JSON are commonly used encodings for spatial data on the web. The
HTML and JSON requirements classes specify the encoding of resource representations using:

- HTML
- JSON

Neither of these encodings is mandatory. An implementer of the API-Common Standard may decide to
implement other encodings instead of, or in addition to, these two.

The Encoding Requirements Classes are specified in [Clause 10 Requirements Class “HTML”](#clause-10)
and [Clause 11 Requirements Class “JSON”](#clause-11).

## 2.4 OpenAPI 3.0 Requirements Class

The OGC API — Common Standard does not mandate any encoding or format for the formal definition of the
API. The preferred option is the OpenAPI 3.0 specification. The OpenAPI 3.0 requirements class has been
specified for APIs implementing OpenAPI 3.0.

The OpenAPI 3.0 Requirements Class is specified in [Clause 12 OpenAPI 3.0 Requirements Class](#clause-12).

## 2.5 OGC Building Blocks Registry

To facilitate the discovery and management of the building blocks specified in this and other OGC API
Standards, a registry has been established at [https://blocks.ogc.org](https://blocks.ogc.org).
