# PRAXO-CORE for COBOL

PRAXO-CORE is an embeddable, MIT-licensed agent framework. This package is its native GnuCOBOL Core: an in-process agent loop with tools, policy, middleware, events, checkpoints, and human-in-the-loop decisions, implemented in COBOL rather than bridged to another Core.

## At a glance

| Field | Value |
| --- | --- |
| Package | `praxo-core-cobol` |
| Registry | Source |
| Build | Source build (see README) |
| Source version | `0.9.0` |
| Published version | not published |
| Source tag | `cobol/v0.9.0` |
| Tier | Core |
| Contract | `SPEC_VERSION` `0.2.0` |
| Documentation | https://axisvela.github.io/praxo-core/languages/cobol/ |
| License | MIT |

## Highlights

- OpenAI-compatible model: native (transport seam)
- Anthropic model: native (transport seam)
- Gemini model: native (transport seam)
- MCP client: native (transport seam)
- Harmovela sink: native (transport seam)
- OpenTelemetry sink: native (transport seam)
- Subagent delegation: native (synchronous seam)
- Retriever: native

## Quick start

This implementation is source-only. Follow the build instructions in [`language/cobol/README.md`](language/cobol/README.md).

## What's included

| Capability | Status | Detail |
| --- | --- | --- |
| OpenAI-compatible model | native (transport seam) | `praxo-openai`; caller supplies a transport program and an optional delta program; SSE streaming reassembles content, tool calls, usage, and finish reason; the model callback lacks tool specs/history |
| Anthropic model | native (transport seam) | `praxo-anthropic`; caller supplies a transport program; maps system messages, tools, tool choice, text, tool use, and usage |
| Gemini model | native (transport seam) | `praxo-gemini`; caller supplies a transport program; maps system instructions, tools, tool choice, text, function calls, usage, and Gemini SSE streaming |
| MCP client | native (transport seam) | `praxo-mcp`; caller supplies a transport program |
| Harmovela sink | native (transport seam) | `praxo-harmovela`; caller supplies a transport program |
| OpenTelemetry sink | native (transport seam) | `praxo-otel`; caller supplies an OTLP/HTTP transport program |
| Subagent delegation | native (synchronous seam) | `praxo-delegation`; synchronous runner callback; no asynchronous manager |
| Retriever | native | `praxo-retriever`; callback seam over query and limit |

## Examples

Runnable examples live under [`language/cobol/examples`](language/cobol/examples).

| Example | What it shows |
| --- | --- |
| [batch-exception-review](language/cobol/examples/batch-exception-review) | Keep the main batch deterministic and hand exceptions to a separate review step. This fixture uses Python to stand in for the batch and scheduler, and reuses the native COBOL [a... |
| [checkpoint](language/cobol/examples/checkpoint) | This example uses the COBOL Core checkpoint allowlist to encode and decode only registered payload types. |
| [consumer](language/cobol/examples/consumer) | This example runs a deterministic model against the COBOL Core, registers one `record(target)` tool, applies an explicit tool scope plus policy, and checks that an allowed call... |
| [event-sink](language/cobol/examples/event-sink) | This example uses the COBOL Core event contract to multicast lifecycle and tool events and filter the tool-only stream. |
| [hitl](language/cobol/examples/hitl) | This example demonstrates a write tool that requires human approval: |
| [identity-policy](language/cobol/examples/identity-policy) | This example uses the COBOL Core path policy to allow an in-root action and reject traversal outside the granted root. |
| [live-model](language/cobol/examples/live-model) | This scaffold wires `praxo-openai` and a `get_time(zone)` tool, but **does not connect to a model out of the box**. The shipped `live-transport` stub returns `PROVIDER_HTTP` wit... |
| [mcp](language/cobol/examples/mcp) | This example uses a caller-owned in-process transport with the COBOL MCP client. It covers initialize, `tools/list`, and `tools/call` without a server process. |
| [provider-fallback](language/cobol/examples/provider-fallback) | This example calls a fallback only after the primary fails and preserves the primary failure when both fail. |
| [retry](language/cobol/examples/retry) | This example retries a transient failure with a bounded attempt count and keeps the exhausted failure state. |
| [service](language/cobol/examples/service) | This example defines a transport-neutral request handler boundary with health, principal, and run cases. Wire it into any COBOL HTTP server. |
| [session-checkpoint](language/cobol/examples/session-checkpoint) | This example saves and restores a conversation history across two agent turns. It uses the Core allowlist for payload encoding and a teaching in-memory payload. |
| [streaming](language/cobol/examples/streaming) | This example accumulates stream chunks and checks that they reconstruct the final output. |
| [structured-output](language/cobol/examples/structured-output) | This example validates a final JSON answer against a schema and rejects invalid output. |

## Scenario Tutorials

Scenario-oriented tutorials live under `language/cobol/Tutorial`. Planning context: [Tutorial Plan](https://axisvela.github.io/praxo-core/getting-started/tutorial-plan/), [100 candidate agent scenarios](https://axisvela.github.io/praxo-core/getting-started/agent-scenarios/), and [Tutorial Catalog](https://axisvela.github.io/praxo-core/getting-started/tutorial-catalog/).

| Path | What it shows |
| --- | --- |
| [Tutorial](language/cobol/Tutorial) | Application tutorials live in `Tutorial/`, alongside focused `language/go/examples/`. |
| [batch-exception-review](language/cobol/Tutorial/batch-exception-review) | This tutorial reuses the existing [`language/cobol/examples/batch-exception-review`](https://github.com/axisvela/praxo-core/tree/main/language/cobol/examples/batch-exception-rev... |
| [budget-review](language/cobol/Tutorial/budget-review) | Flags fixed budget variances and milestone mismatches. No audit conclusion or official determination. |
| [legacy-migration](language/cobol/Tutorial/legacy-migration) | Inventories three fixed modules and reports activation and batch counts. No code conversion or production migration. |
| [medical-coding](language/cobol/Tutorial/medical-coding) | Checks three fixed records for completeness and drafts review-only codes. No reimbursement optimization, billing submission or clinical decision. |

## Reference Applications

Complete AI-native reference applications live under `language/cobol/application`.

| Path | What it shows |
| --- | --- |
| [application](language/cobol/application) | A native GnuCOBOL batch reviewer where the agent drives the primary exception workflow: the driver reads a bounded exception file, the agent inspects each allowed record, writes... |

## Verify

Run the checks from `language/cobol`:

```sh
python language/cobol/run-tests.py
```

This mirror contains the language source and the shared `spec/` vectors, so the implementation can be built and tested here. See [`language/cobol/README.md`](language/cobol/README.md) for the exact commands. The monorepo CI runs conformance, API snapshot, and native tests for this implementation.

## Community

- X: <https://x.com/axisvela>
- Weibo: <https://weibo.com/u/1936025761>
- LinkedIn: <https://www.linkedin.com/company/axisvela/>
- Facebook: <https://www.facebook.com/profile.php?id=61596905732406>
- YouTube: <https://www.youtube.com/@axisvela>
- Discord: <https://discord.com/channels/1575163993767809064/1575164343148875977>
- GitHub Discussions: <https://github.com/axisvela/praxo-core/discussions>
- GitHub Issues: <https://github.com/axisvela/praxo-core/issues>
- Documentation: <https://axisvela.github.io/praxo-core/>
- Architect: <https://axisvela.architect.pub>

## Repository layout

- `language/cobol/` — implementation source, tests, API snapshot, and examples
- `spec/` — shared contract, vectors, and parity inventories
- `LICENSE` — MIT license

## Canonical source

- Canonical source: https://github.com/axisvela/praxo-core/tree/main/language/cobol
- Registry introduction: `language/cobol/REGISTRY.md`
- Machine-readable entry: `language/cobol/llms.txt` and `language/cobol/llms.md`
- Mirror repository: https://github.com/axisvela/praxo-core-cobol
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical COBOL source. The monorepo remains the source of truth and the release workflow source.

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety controller. Do not infer exactly-once execution, complete sandbox isolation, production security certification, live-provider behavior, or physical safety from this package.

MIT licensed.
