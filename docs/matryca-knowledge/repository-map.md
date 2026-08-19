# DeepSeek Harness Repository Map

English | [中文](repository-map.zh.md)

This reference maps the repository by responsibility. It points to the owning documentation instead of maintaining a second inventory of every file.

## Top-level areas

| Area | Responsibility | Authoritative entry |
|---|---|---|
| `packages/` | Product plugins, capability seams, consumers, providers, SDKs, and test support | [Package groups](../../packages/README.md) and each group README |
| `apps/` | Product entry points, the CLI, and the web application | [CLI](../../apps/cli/README.md) and [web test reference](../../apps/web/tests/README.md) |
| `examples/` | Runnable Cordis compositions and protocol demonstrations | [Examples](../../examples/README.md) |
| `python/` | Python client SDK and bundled runtime distribution | [Python SDK](../../python/README.md) |
| `native/` | Native process-confinement sources and packages | [Native components](../../native/README.md) |
| `vendor/` | Pinned Cordis source and the synchronization procedure | [Vendoring policy](../../vendor/README.md) |
| `docs/` | Architecture, subsystem references, cookbooks, user guides, testing, and generated references | [Architecture](../architecture.md), [testing](../testing.md), and [cookbooks](../cookbook/extension-cookbook.md) |
| `.agents/` | Agent workflows and active decision records | [Agent Notes](../../.agents/notes/README.md) |
| `scripts/` | Repository gates, generators, release tooling, and snapshot infrastructure | Root [commands](../../AGENTS.md#commands) and script-local source files |
| `website/` | VitePress projection of selected bilingual documentation | [Website configuration](../../website/docs.ts) |
| `.github/` | CI, release workflows, issue forms, and repository automation | [Workflow directory](../../.github/workflows/) |
| `patches/` | Maintained dependency patches applied by the package manager | [Patch manifest](../../package.json) |
| `assets/` | Small repository assets used by documentation or examples | The consuming document or example |

## Runtime map

The runtime is composed as a Cordis plugin tree. Read [architecture](../architecture.md) before changing package code; use the following families to locate the next document.

| Runtime concern | Package families | What to inspect |
|---|---|---|
| Agent spine | `packages/core/`, `packages/llm/`, `packages/context/`, `packages/compaction/` | Session events, prompt assembly, model streaming, and the agent loop |
| Capabilities | `packages/fs/`, `packages/shell/`, `packages/subprocess/`, `packages/terminal/`, `packages/lsp/`, `packages/web/`, `packages/skill/` | Service Definitions, providers, model-facing consumers, and policy events |
| Durable state | `packages/session/`, `packages/session-query/`, `packages/storage/`, `packages/settings/`, `packages/credentials/`, `packages/attachment/`, `packages/spill/` | Append-only events, projections, bounded retrieval, and persistence backends |
| Collaboration | `packages/interaction/`, `packages/goal/`, `packages/plan/`, `packages/todo/`, `packages/feedback/`, `packages/schedule/` | Human decisions, objectives, plans, feedback, and follow-ups |
| Delegation and work | `packages/subagent/`, `packages/jobs/`, `packages/workflow/`, `packages/code-runtime/` | Child agents, background work, worker threads, and code execution |
| Composition and safety | `packages/bundle/`, `packages/preset/`, `packages/guard/`, `packages/sandbox/`, `packages/boot/`, `packages/identity/` | Profiles, patch layers, lifecycle guards, process confinement, and boot wiring |
| Product transports | `packages/api/`, `packages/host/`, `packages/client/`, `packages/sdk/`, `packages/acp/`, `packages/hooks/` | HTTP, browser, JSON-RPC, ACP, hook bridges, and out-of-process clients |

The complete package and context-key map remains in [packages/README.md](../../packages/README.md). Generated module relationships remain in [module-graph.md](../module-graph.md); do not reproduce that graph manually here.

## Study boundary

The source map includes the vendored directory only through its README and synchronization contract. The vendored implementation is not part of the Matryca projection because it is an imported source copy with its own upstream provenance.

Generated catalogs, lockfiles, build output, snapshots, and local indexes remain derivative or operational data. Study their owning generator or test when needed; do not treat a generated document as the source of the underlying contract.
