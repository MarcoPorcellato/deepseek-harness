# Matryca Knowledge Projection Contract

English | [中文](projection-contract.zh.md)

This reference defines how the DeepSeek Harness fork is admitted to Matryca Knowledge. It keeps source ownership in Git and makes the projected corpus reviewable by commit.

## Authority and identity

The Git repository at [MarcoPorcellato/deepseek-harness](https://github.com/MarcoPorcellato/deepseek-harness) owns the documents and their history. The dedicated documentation branch is the working source for this mapping; the Matryca source manifest selects a ref and resolves it to an immutable commit before checkout and inventory.

A source record is identified by its repository URL and source id, not by a local checkout path. A review records the resolved commit, selected paths, exclusions, classification, and content hashes.

## Admission set

The source manifest admits these authored Markdown families:

| Include | Purpose |
|---|---|
| `README.md`, `AGENTS.md` | Repository-level orientation and standing instructions |
| `docs/**/*.md` | Architecture, references, cookbooks, user guidance, and this mapping |
| `packages/**/README.md` | Package-group and package contracts |
| `examples/**/README.md`, `apps/**/README.md` | Runnable composition and product-entry documentation |
| `python/**/README.md`, `native/**/README.md`, `vendor/**/README.md` | Distribution, security, and vendoring contracts |
| `.agents/notes/README.md`, `.agents/notes/AGENTS.md` | Active decision-record rules |
| `.agents/notes/{proposed,implemented,rejected}/**/*.md` | Active decision records with future decision value |

The manifest excludes generated catalogs and graphs, event inventories, the vendored implementation tree, archived Agent Notes, build output, snapshots, caches, credentials, and runtime logs. The exclusion is applied after inclusion patterns so a broad documentation glob cannot re-admit a forbidden family.

## Review workflow

1. Resolve the selected ref to a commit and record the result.
2. Check out that commit in the Matryca source workspace without using the author's working tree.
3. Inventory only files admitted by the manifest and refuse selected files with uncommitted content.
4. Normalize records, preserve source paths, classify documents, and generate a content-addressed proposal.
5. Review the proposal and relation evidence before applying or publishing a projection.

The projection is not complete merely because checkout succeeds. Review must confirm that the source head, allowlist, exclusions, records, and relation evidence agree.

## Classification

Architecture, development, testing, subsystem, cookbook, and package contract pages are active references or tutorials according to their document type. Root and subtree instruction files are canonical operational guidance. Agent Notes retain their lifecycle classification; archived notes remain outside the default projection.

The map does not convert implementation-status prose into knowledge facts. Current behavior belongs in the owning source document; decision rationale belongs in the active Agent Note.

## Update rule

When this documentation branch changes, regenerate the Matryca proposal from the new exact commit. Do not hand-edit the `knowledge/` projection to repair a source document. If the branch is merged or the default source changes, update the source ref and regenerate the proposal so provenance names the new commit.

## Local verification receipt

Before requesting review, retain:

```sh
git status --short --branch
git rev-parse HEAD
git diff --check
```

The receipt must identify the repository, branch, exact head, selected source ref, inventory result, proposal id, and any skipped quality profile. It must not include credentials or machine-local paths as knowledge content.
