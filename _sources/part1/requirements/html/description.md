## 10.1 Overview

This clause and [Clause 11](#clause-11) specify two requirements classes for encodings that may be used
by an OGC Web API implementation. These encodings are commonly used for spatial data on the web
applications:

- HTML (this clause)
- JSON ([Clause 11](#clause-11))

Neither of these encodings are mandatory. An implementation of the OGC API — Common Standard may
implement one, both, or none of them. Other encodings are possible.

## 10.2 HTML encoding

Geographic information that is only accessible in formats such as GeoJSON or GML have two issues when
web application principles are considered:

- The data are not discoverable using Web crawlers and search engines,
- The data cannot be viewed directly in a browser — additional tools are required to view the data.

Therefore, sharing data on the Web should include publication in HTML. To be consistent with the Web,
this publication should be done in a way that enables users and search engines to discover and access
all of the data.

This is discussed in detail in the W3C/OGC SDW Best Practice. Therefore, the OGC API — Common Standard
recommends supporting HTML as an encoding.

The HTML encoding is specified by requirements [`/req/html/definition`](#req-html-definition) and
[`/req/html/content`](#req-html-content), listed in the [Requirements](#req-clause-10-requirements)
section below, and by the following recommendation.

| **Recommendation 17** | `/rec/html/schema-org` |
|---|---|
| **A** | A 200-response with the media type `text/html`, SHOULD include Schema.org annotations. |

<!-- requirements -->
