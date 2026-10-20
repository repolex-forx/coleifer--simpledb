# Repolex Knowledge Graph of coleifer/simpledb

RDF knowledge graph data for [coleifer/simpledb](https://github.com/coleifer/simpledb), parsed by [repolex](https://repolex.ai).

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
rlex download coleifer/simpledb
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── bf674ccf8bdc45a7cf4e850985a18199accbe770
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── bf674ccf8bdc45a7cf4e850985a18199accbe770
│           └── chunk-001.nq.gz
├── blob
│   ├── 02d9cb9031a2fc8910dd8818ddfb2a89ec17b4f9.nq.gz
│   ├── 06d036f67d3acd8160d3dd177d8fde494d2af84b.nq.gz
│   ├── 6044959e4a6ed9bbf96add3b9048c283f44ff264.nq.gz
│   ├── 84c5581796b18b5c1638a0168cec3198f0854f3d.nq.gz
│   ├── 8b9a8f4ac12f94f7464a35c8f5a187042f6e00ed.nq.gz
│   ├── 98524dcc3699b2c89c7e9a3c313999a9afd7e15f.nq.gz
│   ├── a9fb48ac4040e64996421cec59db48f859c717d1.nq.gz
│   ├── bb3ec5f0d4c70ef732aa4d399282a5ddb2a008fd.nq.gz
│   └── dead0c87243e108e59a026146e4282ec52c62956.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── bf674ccf8bdc45a7cf4e850985a18199accbe770.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 17 files
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

[coleifer/simpledb](https://github.com/coleifer/simpledb)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
