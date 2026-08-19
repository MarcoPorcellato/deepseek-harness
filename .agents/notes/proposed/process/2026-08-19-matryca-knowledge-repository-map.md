# Agent Note: Matryca Knowledge repository map

Status: proposed

## Problem

DeepSeek Harness spans plugins, runnable compositions, SDKs, native launchers, vendored source, documentation, and repository gates. A projection that lists files without their ownership and evidence path would make the corpus large without making the system easier to study or verify.

## Proposal

Maintain a dedicated documentation branch with a semantic repository map, ordered study and test paths, a Matryca projection contract, and an evidence matrix. Keep source code and package contracts authoritative in DeepSeek Harness, admit authored Markdown through an explicit allowlist, and resolve every review to an immutable Git commit.

The documentation branch groups navigation by responsibility and links to existing package, subsystem, cookbook, example, SDK, native, vendoring, and Agent Note owners. It excludes generated catalogs, build output, local indexes, runtime logs, credentials, the vendored implementation tree, and archived Agent Notes from the default projection.

## Alternatives considered

**Only project the default branch documentation.** This keeps the source ref simple but cannot carry the mapping contract while it is being developed and reviewed. The dedicated branch gives the source manifest an explicit review target.

**Import the whole repository into Matryca Knowledge.** This would duplicate implementation and generated data, weaken source ownership, and admit operational or secret-bearing paths. The allowlist preserves the authored documentation plane instead.

**Write the map only in Matryca Knowledge.** This would detach navigation and provenance rules from the source they describe. Keeping the map in DeepSeek Harness lets the source commit explain its own projection and keeps the Matryca registry as the integration configuration.

## Acceptance criteria

- The branch contains a bilingual navigation layer under `docs/matryca-knowledge/`.
- The map covers the top-level repository areas, package families, runnable paths, SDK/native/vendoring layers, documentation ownership, and evidence tiers without copying generated inventories.
- The projection contract states the allowlist, exclusions, immutable-commit rule, classification, and update workflow.
- Every new active document has its required Chinese counterpart and pairing record.
- Documentation checks and link checks pass for the changed scope, and the final diff excludes `vendor/` content changes.

## Risks

The source branch can diverge from the fork default if the Matryca manifest continues to resolve `master`; the registry must name the reviewed ref and regenerate proposals after branch changes. The bilingual pair adds maintenance work, and a broad allowlist can still grow quickly as package READMEs change, so generated catalogs and archived records remain excluded.
