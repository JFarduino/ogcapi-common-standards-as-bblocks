# OGC API - Common - Part 1: Core, as Building Blocks

This repository contains [OGC API — Common — Part 1: Core](https://docs.ogc.org/is/19-072/19-072.html)
(OGC 19-072, version 1.0.0) authored as [OGC Building Blocks](https://ogcincubator.github.io/bblocks-docs/):
every clause, requirements class, term, reference and annex of the Standard is a Building Block, and the
HTML standards document is generated from them.

The Building Blocks are processed by [bblocks-postprocess](https://github.com/opengeospatial/bblocks-postprocess)
(validation, documentation, register), which runs [bblocks-specgen](https://github.com/ogcincubator/bblocks-specgen)
as a build plugin to assemble the standards document described in [`standards.yaml`](standards.yaml).

## Repository layout

```
standards.yaml                 document metadata (title, OGC 19-072, editors, URIs) + clause order
bblocks-config.yaml            register config: identifier prefix, imports, specgen build plugin
_sources/part1/
├── clauses/                   prose, terms and references clauses (1-7 and 13)
│   ├── scope/  conformance/  references/  terms/  abbreviated-terms/
│   ├── conventions/  overview/  media-types/
├── requirements/              requirements classes (clauses 8-12)
│   ├── core/  landing-page/  html/  json/  oas30/
│       { bblock.json, description.md, requirements.yaml, tests.yaml }
├── annexes/                   informative annexes B-G
│   ├── examples/  glossary/  bnf/  web-api-guidelines/  revision-history/  front-matter/
└── test-resources/            test resources of the abstract tests (examples of OGC 19-072 Annex B)
```

Building Block identifiers are `ogc.api.common.part1.<path>` (e.g.
`ogc.api.common.part1.requirements.core`). The requirements reference the reusable OGC API — Common
components (`ogc.api.common.part1.schemas.*`, `.paths.*`, `.responses.*`) of the
[OGC API — Common Building Blocks register](https://ogcincubator.github.io/bblocks-ogcapi-common/),
imported as `@ogc/ogcapi-common`.

### How OGC 19-072 maps to the generated document

- Clauses 1–9 keep the numbering of OGC 19-072. The generator renders each requirements class as its own
  clause, so the HTML and JSON requirements classes (10.2 and 10.3 in OGC 19-072) are clauses 10 and 11,
  OpenAPI 3.0 is clause 12 and Media Types clause 13.
- Requirements (`/req/...`) are in `requirements.yaml` and rendered as requirement boxes. Recommendations
  and permissions (`/rec/...`, `/per/...`) are in `description.md`, next to the text they belong to, so
  that they keep their own numbering and do not appear as tests in the Abstract Test Suite.
- Annex A (Abstract Test Suite) is generated: one entry per requirement, with the test purpose and
  method of the corresponding abstract test of OGC 19-072 (`tests.yaml` of each requirements class).
- The front matter of OGC 19-072 (preface, security considerations, submitters) is in Annex G; the
  abstract and keywords are on the cover page.

## Building

Requires Docker. The postprocessor image is only published for `linux/amd64`: on Apple Silicon, set
`DOCKER_DEFAULT_PLATFORM=linux/amd64` (Docker Desktop emulates it).

```shell
# Build (validation, register, documentation and the standards document)
DOCKER_DEFAULT_PLATFORM=linux/amd64 ./build.sh

# Generated standards document
open build/standards/part1/index.html

# Optional: browse the Building Blocks (and the document) in the viewer at http://localhost:9090
./view.sh
```

From a terminal, the first build asks for permission to install the `bblocks-specgen` plugin. In
scripts/CI, pass `--skip-permissions true` to `./build.sh` instead.

Outputs:

- `build/standards/part1/index.html` — the generated OGC 19-072 document (`report.json` next to it lists
  how each Building Block was used);
- `build-local/` — register, documentation, annotated schemas and validation reports (local builds only).

On GitHub, the `Validate and process Building Blocks` workflow builds and publishes everything to GitHub
Pages on every push to `master` (the template's mechanism is unchanged, see [USAGE.md](USAGE.md)).
