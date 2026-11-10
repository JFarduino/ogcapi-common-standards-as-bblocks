
# Abstract Test Suite (Clause)

`ogc.api.common.part1.annexes.ats` *v1.0.0*

Annex A of OGC API - Common - Part 1: Core: conformance classes and abstract tests. The tests are defined in the requirements classes (abstract-tests); this block lays out the annex.

[*Status*](http://www.opengis.net/def/status): Stable

## Description

# Introduction

OGC Web APIs are not Web Services in the traditional sense. Rather, they define the behavior and
content of a set of Resources exposed through a Web Application Programming Interface (Web API).
Therefore, an API may expose resources in addition to those defined by the standard. A test engine
must be able to traverse the API, identify and validate test points, and ignore resource paths that
are not to be tested.

# Conformance Class Core

<!-- conformance-class: ogc.api.common.part1.requirements.core -->

## HTTP

<!-- abstract-test: core/http -->

## Query Parameters

<!-- abstract-test: core/query-param-name-unknown -->

> **NOTE 1** The parameter name chosen should not fall within the range allowed by
> `/per/core/query-param-name-specified` or `/per/core/query-param-name-tolerance`.

<!-- abstract-test: core/query-param-value-invalid -->

> **NOTE 2** The parameter values chosen should not fall within the range allowed by
> `/per/core/query-param-value-specified` or `/per/core/query-param-value-tolerance`.

<!-- abstract-test: core/query-param-capitalization -->

<!-- abstract-test: core/query-param-list-delimiter -->

<!-- abstract-test: core/query-param-list-escape -->

<!-- abstract-test: core/query-param-list-empty -->

<!-- abstract-test: core/query-param-value-boolean -->

<!-- abstract-test: core/query-param-value-integer -->

<!-- abstract-test: core/query-param-value-decimal -->

<!-- abstract-test: core/query-param-value-double -->

# Conformance Class Landing Page

<!-- conformance-class: ogc.api.common.part1.requirements.landing-page -->

## Landing Page

<!-- abstract-test: landing-page/root-op -->

<!-- abstract-test: landing-page/root-success -->

## API Definition

<!-- abstract-test: landing-page/api-definition-op -->

<!-- abstract-test: landing-page/api-definition-success -->

## Conformance Declaration

<!-- abstract-test: landing-page/conformance-op -->

<!-- abstract-test: landing-page/conformance-success -->

# Conformance Class JSON

<!-- conformance-class: ogc.api.common.part1.requirements.json -->

## JSON Definition

<!-- abstract-test: json/definition -->

## JSON Content

<!-- abstract-test: json/content -->

# Conformance Class HTML

<!-- conformance-class: ogc.api.common.part1.requirements.html -->

## HTML Definition

<!-- abstract-test: html/definition -->

## HTML Content

<!-- abstract-test: html/content -->

# Conformance Class OpenAPI 3.0

<!-- conformance-class: ogc.api.common.part1.requirements.oas30 -->

<!-- abstract-test: oas30/completeness -->

<!-- abstract-test: oas30/exceptions-codes -->

<!-- abstract-test: oas30/oas-definition-1 -->

<!-- abstract-test: oas30/oas-definition-2 -->

<!-- abstract-test: oas30/oas-impl -->

<!-- abstract-test: oas30/security -->

## Sources

* [OGC 19-072 — OGC API - Common - Part 1: Core — Abstract Test Suite](https://docs.ogc.org/is/19-072/19-072.html#_abstract_test_suite_normative)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-common-standards-as-bblocks](https://github.com/JFarduino/ogcapi-common-standards-as-bblocks)
* Path: `_sources/part1/annexes/ats`

