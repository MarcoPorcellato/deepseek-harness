---
type: Document
---
# Matryca upstream source pin

English | [中文](upstream-sync.zh.md)

This reference identifies the immutable upstream release used by the current Matryca documentation integration. It records provenance and compatibility requirements without changing upstream ownership or implying official endorsement.

## Current source

| Field | Value |
|---|---|
| Official repository | [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) |
| Official release | [`dsh-v0.1.0-rc.8`](https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.1.0-rc.8) |
| Official commit | `141eb6fef83422698aef7a981029e843e8161534` |
| Fork mirror | `MarcoPorcellato/deepseek-harness` branch `master` |
| Matryca integration branch | `matryca/dsh-v0.1.0-rc.8-r1` |
| Matryca Knowledge source id | `deepseek-harness` |
| Reviewed source ref | `matryca/dsh-v0.1.0-rc.8-r1`, resolved to an exact commit before inventory |

## Ownership

The official repository owns runtime behavior, package contracts, release artifacts and upstream history. The versioned Matryca branch adds the navigation, evidence and projection documents under this directory plus the reviewed OKF metadata required by Matryca Knowledge.

The fork `master` branch remains a fast-forward mirror of official upstream. A Matryca integration branch never establishes a new upstream release or compatibility promise.

## Runtime compatibility

The rc.8 release declares its SQLite storage format incompatible with rc.7. Qualification uses a disposable DSH home and never opens operator-owned rc.7 data in place. Any data migration requires a separate backup, migration plan and runtime receipt.

“DeepSeek Harness” describes the upstream project and this fork's relationship to it. Matryca naming and promotion must follow the upstream [brand usage guidelines](https://github.com/deepseek-ai/deepseek-harness/blob/dsh-v0.1.0-rc.8/BRAND_GUIDELINES.md) and must not imply endorsement, cooperation or authorization.

## Update procedure

1. Resolve an immutable official release tag and record its exact commit.
2. Build a new versioned Matryca integration branch from that commit without rewriting an earlier integration branch.
3. Reapply the Matryca documentation and OKF adaptations, then regenerate every affected derived document from its owning generator.
4. Run source documentation, OKF and disposable-runtime checks against the exact integration commit.
5. Update the Matryca Knowledge source ref and regenerate its reviewed projection through the managed proposal workflow.

## Rollback

The retained rc.7 documentation source is branch `docs/matryca-knowledge-map` at `6d2cc057338c412500c82729d746422615d2fe0f`. A rollback selects that exact source and regenerates the Knowledge proposal; it does not require a second complete local checkout or a manual edit under `knowledge/`.
