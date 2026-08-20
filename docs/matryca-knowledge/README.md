---
type: Document
---
# DeepSeek Harness and Matryca Knowledge

English | [中文](README.zh.md)

This directory is the navigation layer for studying DeepSeek Harness through Matryca Knowledge.

The DeepSeek Harness repository remains the source of truth for source code, package contracts, tests, examples, runtime artifacts, and decision records. Matryca Knowledge receives a reviewed, provenance-preserving projection of selected Markdown documents; it does not replace this repository.

## Documents

| Document | Scope |
|---|---|
| [Repository map](repository-map.md) | The repository's semantic areas, ownership, and authoritative documentation homes |
| [Study and test paths](study-and-test-paths.md) | Ordered routes from architecture to runnable behavior and evidence |
| [Projection contract](projection-contract.md) | The allowlist, exclusions, provenance rules, and review workflow for Matryca Knowledge |
| [Evidence matrix](evidence-matrix.md) | Test tiers, entry paths, observable outputs, and receipts worth retaining |

## How to use this map

1. Start with [architecture](../architecture.md) to learn plugin composition, profiles, the agent loop, session events, and capability seams.
2. Use the [repository map](repository-map.md) to choose the owning package group or runtime area.
3. Follow a [study and test path](study-and-test-paths.md) until a real entry path produces an observable result.
4. Record the exact source commit and evidence described by the [projection contract](projection-contract.md) and [evidence matrix](evidence-matrix.md).

## Scope boundary

The map documents relationships and navigation; it does not duplicate generated catalogs, package API declarations, test inventories, or implementation details owned by descendant documents.

The Matryca projection includes human-authored Markdown selected by the source manifest. It excludes generated reports, build output, credentials, runtime logs, the vendored Cordis source copy, and archived Agent Notes except where a reviewed source explicitly links to a historical record.

The source manifest resolves the branch to an immutable commit before inventory and review. A projection is therefore attributable to a Git object, not to an unverified working tree or a mutable local path.

## Related source documents

- [Architecture](../architecture.md)
- [Testing policy](../testing.md)
- [Development workflow](../development.md)
- [Package groups](../../packages/README.md)
- [Runnable examples](../../examples/README.md)
- [Agent Notes](../../.agents/notes/README.md)
