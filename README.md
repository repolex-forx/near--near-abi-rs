# Repolex Knowledge Graph of near/near-abi-rs

RDF knowledge graph data for [near/near-abi-rs](https://github.com/near/near-abi-rs), parsed by [repolex](https://repolex.ai).

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
rlex download near/near-abi-rs
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 081a41c28ed20fd838299c0b5dfb2480659ef340
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 081a41c28ed20fd838299c0b5dfb2480659ef340.nq.gz
│   └── repolex
│       └── 081a41c28ed20fd838299c0b5dfb2480659ef340
│           └── chunk-001.nq.gz
├── blob
│   ├── 06bcfe6204c6be366bd289e1e5bba3d66adcf536.nq.gz
│   ├── 0bc9597f87ed82ea20c41f0cd7d81a465186233c.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 2664791bf48b02967eaf57908201966b2dc3b17b.nq.gz
│   ├── 3ed0516317325f34fe30d6984578a7c829e12b4b.nq.gz
│   ├── 4fffb2f89cbd8f2169ce9914bd16bd43785bb368.nq.gz
│   ├── 54fa3c217873cb7a600a65f2a799a990998d26d7.nq.gz
│   ├── 75daeee19f20c89fb32441432b2fb4042255f1dd.nq.gz
│   ├── 85e4101a7652d8feb9b5717056fa117e454c62eb.nq.gz
│   ├── 8b516e84cca688002ae4115ed8f734982d1ea650.nq.gz
│   ├── 8d35e303dd3081c78967fe2436002da219629cef.nq.gz
│   ├── a99a8d273921c2d77242c2a1927f87820e3eda9b.nq.gz
│   ├── c1e29a11a66c1331e6ef196322f3abcae37d8dc8.nq.gz
│   └── c25d0c9d2354d1ce6d3b1df7dd4f4da3930e84ca.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 081a41c28ed20fd838299c0b5dfb2480659ef340.nq.gz
├── filetree
│   └── 081a41c28ed20fd838299c0b5dfb2480659ef340.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 24 files
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

[near/near-abi-rs](https://github.com/near/near-abi-rs)

---
*Parsed on 2026-11-22 by [repolex](https://repolex.ai)*
