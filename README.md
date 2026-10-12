# Repolex Knowledge Graph of Pylons/pyramid_mako

RDF knowledge graph data for [Pylons/pyramid_mako](https://github.com/Pylons/pyramid_mako), parsed by [repolex](https://repolex.ai).

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
rlex download Pylons/pyramid_mako
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 7619ef2a5d9fe7edb57bd326d70048d6cdbca326
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 7619ef2a5d9fe7edb57bd326d70048d6cdbca326
│           └── chunk-001.nq.gz
├── blob
│   ├── 142b6ca357fee89f09803fc9ad7ff676500c37cf.nq.gz
│   ├── 146736ff81600e05e8197ff26f0010f9c88ad2cd.nq.gz
│   ├── 177447227e84734ed666afdae117b5a5053e13f6.nq.gz
│   ├── 178e49f67b79e740fbd6916b4434a922df97a9a1.nq.gz
│   ├── 25d6e60578e3de0d4f5e70d851be101c0690a537.nq.gz
│   ├── 2eca7049f08aadc6b130eee3a147434f3f207695.nq.gz
│   ├── 30101f1389260f611e888c2dd15aee9fd65e3cfb.nq.gz
│   ├── 3a5087f00a3fa41fff78c9e2676da39caa1d1e46.nq.gz
│   ├── 3b2cd8869ab7bbbea08845ef9c3ceb56b59b0335.nq.gz
│   ├── 3bef88bf836b3116c9b79480615d8ad8e78a10a9.nq.gz
│   ├── 44913da3504d2b689b48f73d0bbe2a9da5b23e7e.nq.gz
│   ├── 53edd71ed1ba7ffad449326b6104f02683fd8bb0.nq.gz
│   ├── 54ab1b7828da2c81c148518a7334b648ce96e813.nq.gz
│   ├── 5737055179c779b424f85fe92776d847c5e82905.nq.gz
│   ├── 5ad1ce2804ecc5f88bcfd2280e42cc417f6c124c.nq.gz
│   ├── 5ced96e3b5d11a635acdcf19c4919fb3d70bdf9f.nq.gz
│   ├── 5de32fa7a1769d7c223160baa419bb7067379222.nq.gz
│   ├── 606849326a4002007fd42060b51e69a19c18675c.nq.gz
│   ├── 659df805b39dc1e87e1b2ddde55f39a5fc9dc7df.nq.gz
│   ├── 7a6b6a543f91b17d767308e04c8fc742946a35da.nq.gz
│   ├── 809ba7fd8494ea304509894fd9b7059050ff3d66.nq.gz
│   ├── 84ea77dfde55052a8a1c145424a3e9f9c4285dfe.nq.gz
│   ├── 986553cec01e19d232403b14f343983697f61712.nq.gz
│   ├── 9de95ec92feb0bbfab10fe483b486edcf1363ff9.nq.gz
│   ├── aab76eb9038cc9e389690da463dad69939365e53.nq.gz
│   ├── b1e169dc7c6fb59d182a4bc8fbf179144d509a25.nq.gz
│   ├── bd99a4195b405c862c396e5f72187407ba0a9895.nq.gz
│   ├── be22d2c3de5cb30e8c4774a5f539cb0690739b04.nq.gz
│   ├── cc886805cbc01abbdaecfcda0d7cb4b20bc23e28.nq.gz
│   ├── d3b43b505a99c8a9d3c7f5072e6497474e9bed19.nq.gz
│   ├── d6068824fc26df01d926ee63968362e50294cf41.nq.gz
│   ├── d76c0e4b7fff1b154f59bf5ed4fbdf07a526bfe1.nq.gz
│   ├── e2a7d815b87da95cc0b579b46911a9786913963f.nq.gz
│   ├── f3bbf0be0e77e39d436102f785a088d68a002e79.nq.gz
│   └── fc26ea725ad1ca3ac94f9a6e5d7097697b098101.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 7619ef2a5d9fe7edb57bd326d70048d6cdbca326.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 43 files
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

[Pylons/pyramid_mako](https://github.com/Pylons/pyramid_mako)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
