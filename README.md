# Repolex Knowledge Graph of simonw/files-to-prompt

RDF knowledge graph data for [simonw/files-to-prompt](https://github.com/simonw/files-to-prompt), parsed by [repolex](https://repolex.ai).

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
rlex download simonw/files-to-prompt
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1b234ff6dccb2ca3e56b5c256696558fb85306dc
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1b234ff6dccb2ca3e56b5c256696558fb85306dc
│           └── chunk-001.nq.gz
├── blob
│   ├── 06e1dad0d96ccdf6232899d7da8b20f2c2d4722e.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 3ff5e135f86972cbd2cae703ee38b7b959ceb4d4.nq.gz
│   ├── 52689959119bb338e5da735c014c8872fcfaf00b.nq.gz
│   ├── 7eee04f5794198a822a3f812c065f1441b7ef207.nq.gz
│   ├── 98dcca0c2836ae53d67260be8a5431b855e461bb.nq.gz
│   ├── 9cf07cb2951d96507c23387629c49cc8caf4cff9.nq.gz
│   ├── b76a8aae4b236b2cf4921817c4e407c8dc5e8e5a.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── fc4425036f1aa2181e0efaada7674ce85b59b864.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1b234ff6dccb2ca3e56b5c256696558fb85306dc.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 18 files
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

[simonw/files-to-prompt](https://github.com/simonw/files-to-prompt)

---
*Parsed on 2026-10-15 by [repolex](https://repolex.ai)*
