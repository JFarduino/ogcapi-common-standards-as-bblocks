# OGC API - Common - Part 1: Core, as Building Blocks

This repository contains [OGC API — Common — Part 1: Core](https://docs.ogc.org/is/19-072/19-072.html)
(OGC 19-072, version 1.0.0) authored as [OGC Building Blocks](https://ogcincubator.github.io/bblocks-docs/):
every clause, requirements class, term, reference and annex of the Standard is a Building Block, and the
HTML standards document is generated from them.

The Building Blocks are processed by [bblocks-postprocess](https://github.com/opengeospatial/bblocks-postprocess)
(validation, documentation, register), which runs bblocks-specgen as a build plugin to assemble the
standards document described in [`standards.yaml`](standards.yaml). The plugin is installed from the
`feature/update` branch of [JFarduino/bblocks-specgen](https://github.com/JFarduino/bblocks-specgen), a fork of
[ogcincubator/bblocks-specgen](https://github.com/ogcincubator/bblocks-specgen) that adds the `layout: ogc`
rendering (ModSpec tables, numbered subclauses, OGC cover) and file includes.

## Repository layout

```
standards.yaml                 document metadata (title, OGC 19-072, editors, URIs, notices),
                               layout, preface and clause order
bblocks-config.yaml            register config: identifier prefix, imports, specgen build plugin
_sources/part1/
├── preface/                   preface sections III-VI (I Abstract and II Keywords are generated)
│   ├── preface/  security-considerations/  submitting-organizations/  submitters/
├── clauses/                   prose, terms and references clauses (1-7, 10, 12)
│   ├── scope/  conformance/  references/  terms/  abbreviated-terms/
│   ├── conventions/  overview/  encodings/  media-types/
├── requirements/              requirements classes (8, 9, 10.2, 10.3, 11)
│   ├── core/  landing-page/  html/  json/  oas30/
│       { bblock.json, description.md, requirements.yaml, tests.yaml }
├── annexes/                   Annex A layout, annexes B-F and the closing Bibliography
│   ├── ats/  examples/  glossary/  bnf/  web-api-guidelines/  revision-history/  bibliography/
└── test-resources/            test resources of the abstract tests (examples of OGC 19-072 Annex B)
```

Building Block identifiers are `ogc.api.common.part1.<path>` (e.g.
`ogc.api.common.part1.requirements.core`). The requirements reference the reusable OGC API — Common
components (`ogc.api.common.part1.schemas.*`, `.paths.*`, `.responses.*`) of the
[OGC API — Common Building Blocks register](https://ogcincubator.github.io/bblocks-ogcapi-common/),
imported as `@ogc/ogcapi-common`.

### How OGC 19-072 maps to the generated document

The document is rendered with `layout: ogc` and has the structure and numbering of OGC 19-072: preface
I-VI, clauses 1-12, Annex A (Abstract Test Suite), Annexes B-F and the Bibliography.

- **Clauses.** Clause 10 "Encoding Requirements Classes" is a block of its own (10.1 Overview) with the
  HTML and JSON requirements classes as subclauses 10.2 and 10.3 (`subclauses` in `standards.yaml`).
  Headings in `description.md` carry no number: the layout numbers them, and cross-references use the
  `#sec-<number>` anchors (e.g. `[Clause 8.2](#sec-8.2)`).
- **Statements.** Requirements (with their parts A, B…) and recommendations are in the
  `requirements.yaml` of their class (`type: recommendation`), and are placed in the text with
  `<!-- requirement: <id> -->` / `<!-- recommendation: <id> -->` markers, where OGC 19-072 has them
  (Recommendation 1 of the Core class is placed in clause 6.3). They are numbered in document order:
  Requirements 1-27, Recommendations 1-18. The recommendations that OGC 19-072 identifies as `/per/...`
  carry an explicit `uri`.
- **Annex A.** The conformance classes and abstract tests A.1-A.27 are defined in each
  `requirements.yaml` (`conformance-class`, `abstract-tests`); the `annexes/ats` block lays out the annex
  with `<!-- conformance-class -->` and `<!-- abstract-test -->` markers. `tests.yaml` lists the test
  resources that bblocks-postprocess validates against the schema of the class; abstract tests refer to
  them with `tested-by`.
- **Schemas.** The schemas that OGC 19-072 includes (link, landingPage, confClasses) are not copied:
  they are code blocks with an `include=` option, filled at build time and followed by a link to the
  building block that defines them, e.g.
  ````markdown
  ```yaml include=bblocks://ogc.api.common.part1.schemas.link
  ```
  ````
- **Front and back matter.** The cover carries the notices of the published document
  (`boilerplate.notices`); the informative references are in the closing, unnumbered Bibliography.

Known differences with the published document: Annex A is titled "Annex A (normative) Abstract Test
Suite" (OGC 19-072 has "(informative) … (Normative)"), and in Recommendation 4 the "Statement" row comes
before part A instead of after it.

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

From a terminal, the first build (and the first one after the `pip:` line of the plugin changes) asks
for permission to install the `bblocks-specgen` plugin. In scripts/CI, pass `--skip-permissions true` to
`./build.sh` instead.

The plugin is installed from GitHub (`feature/update`), so changes to bblocks-specgen are picked up once
pushed to that branch. To try a local clone first, put it in `bblocks-specgen-jules/` (ignored by git)
and use `bblocks-specgen @ file:///workspace/bblocks-specgen-jules` as the `pip:` entry in
`bblocks-config.yaml` (`build.sh` mounts the repository on `/workspace`); GitHub workflows cannot see
that folder.

Outputs:

- `build/standards/part1/index.html` — the generated OGC 19-072 document (`report.json` next to it lists
  how each Building Block was used);
- `build-local/` — register, documentation, annotated schemas and validation reports (local builds only).

## Publication

On GitHub, the `Validate and process Building Blocks` workflow builds and publishes everything to GitHub
Pages on every push to `master` (the template's mechanism is unchanged, see [USAGE.md](USAGE.md)); the
repository's Pages source must be set to "GitHub Actions". The site has the Building Blocks viewer at its
root and the standards document under `build/standards/part1/`.
