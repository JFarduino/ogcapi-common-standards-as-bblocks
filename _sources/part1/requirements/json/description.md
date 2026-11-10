JSON is a lightweight data-interchange format designed to facilitate structured data interchange between
applications. JSON is commonly used for Web-based software-to-software interchanges. Most Web developers
are comfortable with using a JSON-based format. Therefore, support for JSON is recommended for
machine-to-machine interactions.

The JSON encoding is specified by requirements [`/req/json/definition`](#req-json-definition) and
[`/req/json/content`](#req-json-content), listed in the [Requirements](#req-clause-11-requirements)
section below, and by the following recommendation.

| **Recommendation 18** | `/rec/json/problem-details` |
|---|---|
| **A** | Any OGC Web API implementation instance returning an RFC 7807 “Problem Details” report in JSON should set the Content-Type header to “application/problem+json” and structure the report using the JSON Schema [here](https://github.com/opengeospatial/ogcapi-common/blob/master/core/openapi/schemas/exception.json). |

An example JSON Schema for the landing page is available at
[landingPage.yaml](http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/schemas/landingPage.yaml)
(see also the [Landing Page schema](bblocks://ogc.api.common.part1.schemas.landingPage) building block).

An example JSON Problem Details report is available at
[ExceptionExample.yaml](http://schemas.opengis.net/ogcapi/common/part1/1.0/openapi/examples/ExceptionExample.yaml)
(see also the [Exception schema](bblocks://ogc.api.common.part1.schemas.exception) building block).

<!-- requirements -->
