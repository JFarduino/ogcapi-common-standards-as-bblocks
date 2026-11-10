
# Media Types (Clause)

`ogc.api.common.part1.clauses.media-types` *v1.0.0*

Clause 12 of OGC API - Common - Part 1: Core: media types for responses, OpenAPI definitions and Problem Details reports.

[*Status*](http://www.opengis.net/def/status): Stable

## Description

## Normal Response Media Types

The typical media type for all “web pages” in an OGC Web API would be `text/html`.

The media type that would typically be used in an OGC Web API for machine-to-machine exchanges would be
`application/json`.

## OpenAPI Media Types

The media types for an OpenAPI definition are `application/vnd.oai.openapi+json;version=3.0` (JSON) and
`application/vnd.oai.openapi;version=3.0` (YAML).

> **NOTE** The OpenAPI media type has not been registered yet with IANA and may change.

## Problem Details Media Types

OGC API — Common recommends that implementers use IETF RFC 7807 when constructing the response body for
an error condition. The media types for an RFC 7807 Problem Details response body are:

- `application/problem+json` — for responses in JSON
- `application/problem+xml` — for responses in XML

## Sources

* [OGC 19-072 — OGC API - Common - Part 1: Core — Media Types](https://docs.ogc.org/is/19-072/19-072.html#mediatypes-section)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-common-standards-as-bblocks](https://github.com/JFarduino/ogcapi-common-standards-as-bblocks)
* Path: `_sources/part1/clauses/media-types`

