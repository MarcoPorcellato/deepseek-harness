# Agent Note: Matryca Knowledge repository map

Status: proposed

English | [中文](2026-08-19-matryca-knowledge-repository-map.zh.md)

## Problem

DeepSeek Harness spans plugins, runnable compositions, SDKs, native launchers, vendored source, documentation, and repository gates. A projection that lists files without their ownership and evidence path would make the corpus large without making the system easier to study or verify.

## Proposal

Maintain a versioned Matryca integration branch for each qualified upstream release. Each branch contains a semantic repository map, ordered study and test paths, a Matryca projection contract, an evidence matrix, and an exact upstream source pin. Keep source code and package contracts authoritative in DeepSeek Harness, admit authored Markdown through an explicit allowlist, and resolve every review to an immutable Git commit.

The versioned branch groups navigation by responsibility and links to existing package, subsystem, cookbook, example, SDK, native, vendoring, and Agent Note owners. It excludes generated catalogs, build output, local indexes, runtime logs, credentials, the vendored implementation tree, and archived Agent Notes from the default projection. The local installation retains one complete checkout at the latest qualified branch; older branch and commit provenance remains in Git and Matryca Knowledge without duplicate worktrees.

## Alternatives considered

**Only project the default branch documentation.** This keeps the source ref simple but mixes the upstream mirror with Matryca-owned documentation. A versioned integration branch gives the source manifest an explicit review target without changing the fork mirror.

**Import the whole repository into Matryca Knowledge.** This would duplicate implementation and generated data, weaken source ownership, and admit operational or secret-bearing paths. The allowlist preserves the authored documentation plane instead.

**Write the map only in Matryca Knowledge.** This would detach navigation and provenance rules from the source they describe. Keeping the map in DeepSeek Harness lets the source commit explain its own projection and keeps the Matryca registry as the integration configuration.

**Retain one complete checkout for each upstream release.** This would simplify offline comparisons but duplicate source trees and dependencies. Immutable Git refs and Knowledge provenance retain the required history with lower local storage cost.

## Acceptance criteria

- The branch contains a bilingual navigation layer under `docs/matryca-knowledge/`.
- The map covers the top-level repository areas, package families, runnable paths, SDK/native/vendoring layers, documentation ownership, and evidence tiers without copying generated inventories.
- The projection contract states the allowlist, exclusions, immutable-commit rule, classification, and update workflow.
- The source pin names the immutable upstream release, the versioned Matryca branch, compatibility requirements, and rollback source.
- Every new active document has its required Chinese counterpart and pairing record.
- Documentation checks and link checks pass for the changed scope, and the final diff excludes `vendor/` content changes.
- The local installation retains one complete checkout at the latest qualified branch after temporary worktrees pass clean-state and reachability checks.

## Risks

Every upstream release requires a new integration branch and a reviewed Knowledge proposal. The bilingual pairs add maintenance work, and a broad allowlist can still grow quickly as package READMEs change, so generated catalogs and archived records remain excluded. Deleting an unverified worktree could lose local work; cleanup therefore requires a clean status and a retained local or remote ref for its exact head.
