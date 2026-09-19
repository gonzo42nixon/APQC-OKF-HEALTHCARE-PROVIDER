# APQC Healthcare Provider PCF as OKF

Machine-readable knowledge graph of the APQC Process Classification Framework (PCF) for Healthcare Providers, version 7.2.1. The corpus contains 1,985 linked process nodes and is designed for human navigation as well as retrieval-assisted reasoning by AI agents.

## Repository contents

| Path | Purpose |
| --- | --- |
| `okf/` | Canonical Markdown nodes with YAML frontmatter |
| `data/apqc_healthcare_provider_pcf.json` | Hierarchical JSON representation |
| `data/apqc_healthcare_provider_pcf_flat.json` | Flat JSON representation for search and retrieval |
| `okf.zip` | Portable bundle accepted by the viewer |
| `viewer/` | Browser-based graph navigator |
| `agent/knowledge-source.json` | Machine-readable knowledge-source descriptor |
| `AGENTS.md` | Retrieval and reasoning guidance for coding/AI agents |
| `NOTICE.md` | Required APQC copyright and attribution notice |

## Node model

Each `okf/<hierarchy_id>.md` file contains YAML metadata and a readable definition. The main fields are:

- `pcf_id`: stable APQC process-element identifier
- `hierarchy_id`: hierarchical position and filename stem
- `type`: `ProcessGroup`, `Process`, `Activity`, or `Task`
- `parent`: hierarchy ID of the parent node; a top-level node refers to itself
- `metrics_available`: whether APQC metrics are indicated as available
- `definition`: source definition of the process element

## Use with AI agents

Point the agent or retrieval pipeline at `agent/knowledge-source.json`. For broad retrieval, index the flat JSON or the Markdown frontmatter and body. Once a candidate is found, load the canonical Markdown node and its parent/children before forming an answer. `AGENTS.md` contains the repository-specific grounding rules.

Example citation: `1.1.1.1 Define and prioritize Service Areas (PCF ID 18758; okf/1.1.1.1.md)`.

## Viewer

Open `viewer/index.html` and select `okf.zip`. When served together from a web server, the viewer can also load the repository bundle automatically.

## Integrity

The imported corpus was validated for unique `hierarchy_id` and `pcf_id` values, valid YAML-style frontmatter, and resolvable parent references.

## Copyright and attribution

This repository contains APQC copyrighted material. Redistribution and derivative works are permitted subject to retaining the complete notice in [NOTICE.md](NOTICE.md).
