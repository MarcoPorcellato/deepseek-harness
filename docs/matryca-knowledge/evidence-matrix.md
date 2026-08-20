---
type: Document
---
# Evidence Matrix

English | [中文](evidence-matrix.zh.md)

This reference maps a claim about DeepSeek Harness to the smallest evidence that can support it and the stronger evidence needed before release or external publication.

| Claim | First evidence | Stronger evidence | Owning source |
|---|---|---|---|
| A package type-checks and its lifecycle is local-safe | Focused package tests and `pnpm run typecheck` | CI result for the exact head | Package README and tests |
| A plugin is present in a product composition | Loader/config smoke and `--dump-config` output | Built entry-path test through the published artifact | Profile, bundle, and example README |
| A turn is model-visible and replayable | Keyless snapshot plus session-log assertion | With-key smoke against the real provider | [Testing policy](../testing.md) and session package |
| A tool changes the external world correctly | Real executor with a controlled fixture and external re-read | With-key e2e that verifies files, processes, or protocol state | Tool package README and e2e suite |
| A wire or SDK contract holds | JSON-RPC/ACP replay or protocol test | Built runtime and Python package smoke | SDK, ACP, Python, and example READMEs |
| A confinement claim holds | Focused native or sandbox test on the target platform | Platform CI and release artifact receipt | Native and sandbox READMEs |
| Documentation is synchronized | `pnpm run doc-sync` and `git diff --check` | Reviewed Matryca proposal from an immutable source commit | This directory and Matryca source policy |

## Receipt fields

Each evidence item kept for study or review records:

- exact Git head and branch or tag;
- command, test selector, and exit status;
- platform, Node, pnpm, Python, and relevant tool versions;
- whether the run was keyless, with-key, replayed, or skipped;
- artifact, transcript, or external-world observation path;
- failure, limitation, or coverage gap.

Do not store API keys, tokens, local filesystem paths, or unreviewed runtime logs in the projected corpus. A successful local run is evidence for that environment; it is not a platform or release claim.

## Reading a result

`PASS` means the named command and exact head produced the expected observation. `SKIP` means a prerequisite was unavailable and the claim remains unproven. `RUNNING`, historical output, a stale head, or a self-reported agent answer is not a qualification result.

The Matryca projection preserves the source document and review metadata. It does not promote a test result into a permanent fact without its head, scope, and receipt.
