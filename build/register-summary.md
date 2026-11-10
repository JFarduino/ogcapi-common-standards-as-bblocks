# OGC API - Common - Part 1 (Standard as Building Blocks)

OGC API — Common — Part 1: Core (OGC 19-072) authored as Building Blocks: every clause,
requirements class, term, reference and annex of the Standard is a Building Block, and the
standards document is generated from them.


This repository contains the Building Blocks for
[OGC API — Common — Part 1: Core](https://docs.ogc.org/is/19-072/19-072.html) (OGC 19-072, version 1.0.0),
following the "OGC Standards as Building Blocks" approach: normative requirements, abstract tests,
test resources and prose are co-located in Building Blocks, and the HTML standards document is
generated from them by [bblocks-specgen](https://github.com/ogcincubator/bblocks-specgen)
(see `standards.yaml`).

The requirements reference the reusable OGC API — Common components (schemas, paths, responses)
published in the [OGC API — Common Building Blocks register](https://ogcincubator.github.io/bblocks-ogcapi-common/).


## Building Blocks

### `ogc.api.common.part1.annexes.ats` — Abstract Test Suite

**Type:** clause

Annex A of OGC API - Common - Part 1: Core: conformance classes and abstract tests. The tests are defined in the requirements classes (abstract-tests); this block lays out the annex.

### `ogc.api.common.part1.annexes.bibliography` — Bibliography

**Type:** references

Bibliography of OGC API - Common - Part 1: Core (informative references).

### `ogc.api.common.part1.annexes.bnf` — Backus-Naur Forms

**Type:** clause

Annex D of OGC API - Common - Part 1: Core: ABNF for URIs (from IETF RFC 3986).

### `ogc.api.common.part1.annexes.examples` — Examples (Informative)

**Type:** clause

Annex B of OGC API - Common - Part 1: Core: example landing pages, conformance declarations, API definitions and service metadata.

### `ogc.api.common.part1.annexes.glossary` — Glossary

**Type:** clause

Annex C of OGC API - Common - Part 1: Core: glossary of ModSpec terms.

### `ogc.api.common.part1.annexes.revision-history` — Revision History

**Type:** clause

Annex F of OGC API - Common - Part 1: Core: revision history.

### `ogc.api.common.part1.annexes.web-api-guidelines` — OGC Web API Guidelines

**Type:** clause

Annex E of OGC API - Common - Part 1: Core: how the Standard addresses the OGC Web API Guidelines.

### `ogc.api.common.part1.clauses.abbreviated-terms` — Abbreviated terms

**Type:** clause

Clause 5 of OGC API - Common - Part 1: Core: abbreviated terms.

### `ogc.api.common.part1.clauses.conformance` — Conformance

**Type:** clause

Clause 2 of OGC API - Common - Part 1: Core: conformance classes defined by the Standard and how conformance is tested.

### `ogc.api.common.part1.clauses.conventions` — Conventions

**Type:** clause

Clause 6 of OGC API - Common - Part 1: Core: Web API fundamentals, identifiers, links, link relations, use of HTTPS and API definitions.

### `ogc.api.common.part1.clauses.encodings` — Encoding Requirements Classes

**Type:** clause

Clause 10 of OGC API - Common - Part 1: Core: overview of the HTML and JSON encoding requirements classes, which are its subclauses 10.2 and 10.3.

### `ogc.api.common.part1.clauses.media-types` — Media Types

**Type:** clause

Clause 12 of OGC API - Common - Part 1: Core: media types for responses, OpenAPI definitions and Problem Details reports.

### `ogc.api.common.part1.clauses.overview` — Overview

**Type:** clause

Clause 7 of OGC API - Common - Part 1: Core: evolution from OGC Web Services, modular APIs and the ways clients use OGC APIs.

### `ogc.api.common.part1.clauses.references` — Normative references

**Type:** references

Clause 3 of OGC API - Common - Part 1: Core: normative references (the informative ones are in the Bibliography).

### `ogc.api.common.part1.clauses.scope` — Scope

**Type:** clause

Clause 1 of OGC API - Common - Part 1: Core: the scope of the Standard.

### `ogc.api.common.part1.clauses.terms` — Terms and definitions

**Type:** terms

Clause 4 of OGC API - Common - Part 1: Core: terms and definitions.

### `ogc.api.common.part1.preface.preface` — Preface

**Type:** clause

Preface of OGC API - Common - Part 1: Core (preface section).

### `ogc.api.common.part1.preface.security-considerations` — Security considerations

**Type:** clause

Security considerations of OGC API - Common - Part 1: Core (preface section).

### `ogc.api.common.part1.preface.submitters` — Submitters

**Type:** clause

Submitters of OGC API - Common - Part 1: Core (preface section).

### `ogc.api.common.part1.preface.submitting-organizations` — Submitting Organizations

**Type:** clause

Submitting Organizations of OGC API - Common - Part 1: Core (preface section).

### `ogc.api.common.part1.requirements.core` — Core Requirements Class

**Type:** requirements-class

Requirements class "Core": protocol-level conventions applicable to all OGC Web APIs - use of HTTP 1.1, HTTP status codes, query parameter names and values, web caching, cross-origin requests, string internationalization, resource encodings and parameter encoding.

### `ogc.api.common.part1.requirements.landing-page` — Landing Page Requirements Class

**Type:** requirements-class

Requirements class "Landing Page": the landing page, the API definition and the conformance declaration resources of an OGC Web API.

### `ogc.api.common.part1.requirements.html` — Requirements Class “HTML”

**Type:** requirements-class

Encoding requirements class "HTML": HTML 5 representations of the Landing Page and Conformance resources.

### `ogc.api.common.part1.requirements.json` — Requirements Class “JSON”

**Type:** requirements-class

Encoding requirements class "JSON": JSON representations of the Landing Page and Conformance resources. The schema of this building block is the JSON payload of these resources, so that the test resources of the class are validated against it.

### `ogc.api.common.part1.requirements.oas30` — OpenAPI 3.0 Requirements Class

**Type:** requirements-class

Requirements class "OpenAPI 3.0": requirements for APIs that are self-documented using an OpenAPI 3.0 definition.

