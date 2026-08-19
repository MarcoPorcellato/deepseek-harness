# Study and Test Paths

English | [中文](study-and-test-paths.zh.md)

These tutorials turn the repository map into observable study sessions. They assume a macOS or Linux development shell, Node supported by the root `package.json`, and a dependency installation completed with `pnpm install`.

## Path 1: Understand composition

1. Read [the Cordis primer](../cordis-primer.md), then [architecture](../architecture.md).
2. Inspect [profiles and bundles](../architecture.md#profiles-and-bundles) and dump a real composition with `pnpm dsh --profile headless --dump-config`.
3. Read the owning group README for the package that contributes the row you want to understand.
4. Confirm the result by identifying the profile, bundle, patch row, and provider that supplied the runtime service.

The observable result is a configuration tree, not a claim that a plugin is present because its package exists on disk.

## Path 2: Follow one model turn

1. Read [turn flow](../architecture.md#turn-flow), [session log](../architecture.md#session-log), and the [agent lifecycle](../agent-lifecycle.md).
2. Start with `packages/core/agent-loop/`, `packages/core/session/`, `packages/core/system-prompt/`, and `packages/llm/llm/`.
3. Run a keyless snapshot with `pnpm run test:snapshot` and inspect the replayed JSONL and expected output for one scenario.
4. Trace one durable event from append to message derivation and one live event from producer to consumer.

The observable result is a reproducible transcript whose model-visible input can be reconstructed from the session log.

## Path 3: Follow a capability seam

1. Read the [capability seam reference](../capability-seams.md) and [extension cookbook](../cookbook/extension-cookbook.md).
2. Choose one family from the [repository map](repository-map.md), then identify its Service Definition, provider, and consumer.
3. Read the package README and the owning subsystem page before reading implementation files.
4. Run the smallest package tests that cover registration, lifecycle disposal, policy, and the model-facing result.

The observable result is a provider-independent contract with a real consumer and a test that exercises the registration path.

## Path 4: Run an assembled example

1. Read [examples](../../examples/README.md), then choose `headless-agent`, `acp-agent`, or `jsonrpc-agent`.
2. Follow the selected example README and keep the default composition unchanged for the first run.
3. Run the keyless snapshot or built entry-path test named by the example.
4. If a real model key is available, run the example's with-key smoke and verify the external world rather than trusting the agent's self-report.

The observable result is an application-level transcript or external side effect produced through the same composition that ships in the example.

## Path 5: Inspect transports and confinement

1. Read the [Python SDK](../../python/README.md), [native README](../../native/README.md), and [vendoring procedure](../../vendor/README.md) when the question crosses a distribution or security boundary.
2. Inspect `packages/sdk/`, `packages/acp/`, `packages/sandbox/`, `native/landlock-run/`, and the relevant build scripts.
3. Run the narrow protocol, built-artifact, or native checks named by the owning README.
4. Record platform, exact commit, launcher mode, and artifact path with the result.

The observable result is a wire-level response, a built runtime invocation, or a confinement receipt tied to a specific platform.

## Evidence ladder

Use evidence in increasing order of distance from a unit test:

1. Typecheck and focused unit tests establish local type and lifecycle behavior.
2. Coverage, snapshot, and built-entry tests establish assembled and persisted behavior.
3. With-key e2e establishes interaction with the real provider and external world.
4. Platform-specific CI or release artifacts establish claims that a local macOS run cannot prove.

Every retained result records the exact Git head, command, platform, dependency/runtime versions, exit status, and artifact or transcript path. A skipped, historical, or local-only result is not a release qualification.
