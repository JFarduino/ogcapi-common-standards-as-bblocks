
# Conformance (Clause)

`ogc.api.common.part1.clauses.conformance` *v1.0.0*

Clause 2 of OGC API - Common - Part 1: Core: conformance classes defined by the Standard and how conformance is tested.

[*Status*](http://www.opengis.net/def/status): Stable

## Description

Conformance with this Standard shall be checked using the tests specified in [Annex A](#sec-A)
(normative) of this document. The framework, concepts, and methodology for testing, and the criteria to
claim conformance are specified in the OGC Compliance Testing Policies and Procedures and the
[OGC Compliance Testing web site](https://cite.opengeospatial.org/teamengine/). This Standard addresses
one Standardization Target: [Web APIs](#sec-4.9).

OGC API — Common — Part 1: Core provides a common foundation for OGC Web API Standards. The assumption
is that this Standard will only be implemented through inclusion in other Standards. Therefore, all the
relevant abstract tests in Annex A should be included in or referenced by the Abstract Test Suite (ATS)
in each Standard that implements conformance classes defined in this Standard.

This Standard identifies five conformance classes. The conformance classes implemented by an OGC API
are advertised through the `/conformance` resource on the implementation instance of the API’s landing
page. Each conformance class is defined by one requirements class. The tests in Annex A are organized by
Requirements Class. So, an implementation of the Core conformance class must pass all tests specified in
Annex A for the Core requirements class.

## Core Requirements Class

The requirements specified in the Core Requirements Class are applicable to all OGC API Standards. They
assure consistent use of the HTTP protocols, provide rules for the construction of URIs, and define
requirements governing the use and processing of URI query parameters. Through these requirements,
OGC API — Common seeks to assure that implementations of OGC API Standards will provide a predictable
interface for their peers.

The Core requirements class is specified in [Clause 8 Core Requirements Class](#sec-8).

## Landing Page Requirements Class

The requirements specified in the Landing Page Requirements Class provide a minimal useful service
interface for an OGC Web API. These resources convey a basic understanding of the API and provide a
starting point for further discovery. The requirements specified in this requirements class are
recommended for all OGC Web APIs.

The Landing Page requirements class is specified in [Clause 9 Landing Page Requirements Class](#sec-9).

## Encoding Requirements Classes

The OGC API — Common Standard does not mandate a specific encoding or format for representations of
resources. However, both HTML and JSON are commonly used encodings for spatial data on the web. The
HTML and JSON requirements classes specify the encoding of resource representations using:

- HTML
- JSON

Neither of these encodings is mandatory. An implementer of the API-Common Standard may decide to
implement other encodings instead of, or in addition to, these two.

The Encoding Requirements Classes are specified in [Clause 10 Encoding Requirements Classes](#sec-10).

## OpenAPI 3.0 Requirements Class

The OGC API — Common Standard does not mandate any encoding or format for the formal definition of the
API. The preferred option is the OpenAPI 3.0 specification. The OpenAPI 3.0 requirements class has been
specified for APIs implementing OpenAPI 3.0.

The OpenAPI 3.0 Requirements Class is specified in [Clause 11 OpenAPI 3.0 Requirements Class](#sec-11).

## OGC Building Blocks Registry

To facilitate the discovery and management of the building blocks specified in this and other OGC API
Standards, a registry has been established at [https://blocks.ogc.org](https://blocks.ogc.org).

## Sources

* [OGC 19-072 — OGC API - Common - Part 1: Core — Conformance](https://docs.ogc.org/is/19-072/19-072.html#_conformance)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-common-standards-as-bblocks](https://github.com/JFarduino/ogcapi-common-standards-as-bblocks)
* Path: `_sources/part1/clauses/conformance`

