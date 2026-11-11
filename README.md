# Business Intelligence

The common BI vocabulary -- dashboards, the charts or tiles on them, the saved queries and reports behind them, and the data sources they read -- distilled from the APIs that already exist. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Business Intelligence, BI, Data Visualization, Dashboards, Reporting, Data Analytics, Embedded Analytics in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| dashboard | 29 | 28 | name 75%, id 68% | dashboards 21, dashboard 10, workbooks 2 |
| chart | 17 | 15 | id 60%, name 60% | widgets 5, chart 4, charts 3, looks 2 |
| data_source | 18 | 17 | id 71%, name 53%, source_type 53% | datasources 14, data-sources 3, data_sources 2 |

Cohort: 159 providers with harvested OpenAPI, 42 crosswalks. Of the providers exposing a dashboard: 62% create, 86% list, 83% fetch, 52% update, 55% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- BI tools agree on the identity of what they hold and little else: dashboards on name and id, charts on id and name, with description and created_at near 40%. The layout and the query inside are the product, and each tool keeps them its own way.
- Data sources agree on id, name and source_type -- the connection a dashboard reads through.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- chart covers tiles, widgets, cards, questions, looks and panels: one visualization on a dashboard.
- Reports were dropped: the word means a scheduled export at one tool and a dashboard at another.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
