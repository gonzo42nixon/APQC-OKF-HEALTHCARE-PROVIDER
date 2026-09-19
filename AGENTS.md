# Agent guidance for this knowledge graph

Use this repository as a domain knowledge source for healthcare-provider process reasoning.

## Retrieval order

1. Start with `data/apqc_healthcare_provider_pcf_flat.json` for broad search, filtering, and ID lookup.
2. Use `data/apqc_healthcare_provider_pcf.json` when hierarchy and ancestry matter.
3. Read the canonical node in `okf/<top_level>/<hierarchy_id>.md` before citing or reasoning about a specific process element.
4. Preserve both identifiers: `hierarchy_id` expresses the position in the framework; `pcf_id` is the stable APQC process-element identifier.

## Reasoning rules

- Distinguish source facts from recommendations or inferences.
- Cite relevant nodes as `okf/<top_level>/<hierarchy_id>.md` and include the `pcf_id` in the answer.
- Traverse `parent` and child links when the question concerns scope, dependencies, decomposition, or adjacent processes.
- Treat `metrics_available` as an availability indicator, not as a metric value.
- Treat `change_summary` and `differenceIndex` as comparison metadata between PCF v7.2.1 and v6.1.1.
- Do not infer healthcare, legal, regulatory, or clinical requirements that are absent from the graph.
- Retain the copyright and attribution notice in `NOTICE.md` in copies and derivative works.

## Integrity constraints

- A node filename equals its `hierarchy_id` plus `.md`; its directory equals the first numeric segment of that ID.
- `pcf_id` and `hierarchy_id` are unique across the corpus.
- Every non-root `parent` must resolve to another node.
- Do not silently rewrite source definitions.
