
# Requirements Class “JSON” (Requirements-class)

`ogc.api.common.part1.requirements.json` *v1.0.0*

Encoding requirements class "JSON": JSON representations of the Landing Page and Conformance resources. The schema of this building block is the JSON payload of these resources, so that the test resources of the class are validated against it.

[*Status*](http://www.opengis.net/def/status): Stable

## Description

JSON is a lightweight data-interchange format designed to facilitate structured data interchange between
applications. JSON is commonly used for Web-based software-to-software interchanges. Most Web developers
are comfortable with using a JSON-based format. Therefore, support for JSON is recommended for
machine-to-machine interactions.

<!-- requirements-class -->

<!-- requirement: json/definition -->

<!-- requirement: json/content -->

<!-- recommendation: json/problem-details -->

An example JSON Schema for the landing page is available at
[landingPage.yaml](http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/schemas/landingPage.yaml)
(see also the [Landing Page schema](bblocks://ogc.api.common.part1.schemas.landingPage) building block).

An example JSON Problem Details report is available at
[ExceptionExample.yaml](http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/examples/ExceptionExample.yaml)
(see also the [Exception schema](bblocks://ogc.api.common.part1.schemas.exception) building block).

## Schema

```yaml
$schema: https://json-schema.org/draft/2020-12/schema
title: JSON payload of the Landing Page requirements class resources
description: '/req/json/content (OGC 19-072): the JSON payload of a Landing Page or
  Conformance resource SHALL conform with the JSON Schema specified for the resource
  in the Landing Page Requirements Class, i.e. landingPage.yaml for the Landing Page
  and confClasses.yaml for the Conformance Declaration. The test resources of the
  JSON requirements class are validated against this schema.'
anyOf:
- $ref: https://ogcincubator.github.io/bblocks-ogcapi-common/build/annotated/api/common/part1/schemas/landingPage/schema.yaml
- $ref: https://ogcincubator.github.io/bblocks-ogcapi-common/build/annotated/api/common/part1/schemas/confClasses/schema.yaml
x-bblocks-metadata:
  itemIdentifier: ogc.api.common.part1.requirements.json
  register: https://jfarduino.github.io/ogcapi-common-standards-as-bblocks/build/register.json
  version: 1.0.0
  dateOfLastChange: '2026-11-10'

```

Links to the schema:

* YAML version: [schema.yaml](https://jfarduino.github.io/ogcapi-common-standards-as-bblocks/build/annotated/api/common/part1/requirements/json/schema.json)
* JSON version: [schema.json](https://jfarduino.github.io/ogcapi-common-standards-as-bblocks/build/annotated/api/common/part1/requirements/json/schema.yaml)


# JSON-LD Context

```jsonld
{
  "@context": {
    "title": "dct:title",
    "description": "dct:description",
    "conformsTo": {
      "@id": "dct:conformsTo",
      "@type": "@id",
      "@container": "@set"
    },
    "dct": "http://purl.org/dc/terms/",
    "oa": "http://www.w3.org/ns/oa#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "@version": 1.1
  }
}
```

You can find the full JSON-LD context here:
[context.jsonld](https://jfarduino.github.io/ogcapi-common-standards-as-bblocks/build/annotated/api/common/part1/requirements/json/context.jsonld)

## Sources

* [OGC 19-072 — OGC API - Common - Part 1: Core — Requirements Class “JSON”](https://docs.ogc.org/is/19-072/19-072.html#rc_json-section)

# For developers

The source code for this Building Block can be found in the following repository:

* URL: [https://github.com/JFarduino/ogcapi-common-standards-as-bblocks](https://github.com/JFarduino/ogcapi-common-standards-as-bblocks)
* Path: `_sources/part1/requirements/json`

