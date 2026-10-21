# Repolex Knowledge Graph of glue-viz/glue-dataverse

RDF knowledge graph data for [glue-viz/glue-dataverse](https://github.com/glue-viz/glue-dataverse), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download glue-viz/glue-dataverse
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 5e98fb0d78cc17e8f2a1c4b990ebfe5bce8fd00a
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 5e98fb0d78cc17e8f2a1c4b990ebfe5bce8fd00a
│           └── chunk-001.nq.gz
├── blob
│   ├── 2962c5619b24a674d49939160653a5f41f1c92c3.nq.gz
│   ├── 4b269dd6f8352b536b2c8f68c3497c4c1eecced6.nq.gz
│   ├── 74667e3daa62b274fc8f0f33a879e780bab03c7b.nq.gz
│   ├── 8d445604a95ac6a51874b6a1cbc812920719839a.nq.gz
│   ├── a3db2a9c11fbc6e3efe2e6ad3fd41bed32a519a8.nq.gz
│   ├── c92bce705072db8334a60a8c950376c625199a6f.nq.gz
│   ├── df920ed03ca1dd14fd9559c1b9cd19cbd34523d6.nq.gz
│   └── e39bd9355657cf0fec471b9bce19c51c3a710077.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 5e98fb0d78cc17e8f2a1c4b990ebfe5bce8fd00a.nq.gz
├── issue
│   └── issue.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 15 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[glue-viz/glue-dataverse](https://github.com/glue-viz/glue-dataverse)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
