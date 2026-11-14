# PRAXO-CORE for COBOL

A native GnuCOBOL implementation, not a bridge to another Core. All 63 normative vectors across the eleven groups pass, together with native agent, JSON, contract-boundary, behavior, tooling, and API declaration checks. The `cobol-conformance` remote job checks the declared scope. `cobol/v0.6.0` is the source tag. Version `0.6.0` adds Anthropic and Gemini transport-seam model adapters, an OTLP/HTTP OpenTelemetry sink, a retriever seam, and a synchronous delegation seam. Earlier source adds middleware, lifecycle, cancellation, streaming, SSE, batch tool dispatch, MCP, Harmovela, OpenAI-compatible adapters, and human-in-the-loop interrupt decisions.

## At a glance

| Field | Value |
| --- | --- |
| Package | `praxo-core-cobol` |
| Registry | Source |
| Build | Source build (see README) |
| Source version | `0.6.0` |
| Published version | not published |
| Source tag | `cobol/v0.6.0` |
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
| OpenAI-compatible model | native (transport seam) | `praxo-openai`; caller supplies a transport program; the model callback lacks tool specs/history |
| Anthropic model | native (transport seam) | `praxo-anthropic`; caller supplies a transport program; maps system messages, tools, tool choice, text, tool use, and usage |
| Gemini model | native (transport seam) | `praxo-gemini`; caller supplies a transport program; maps system instructions, tools, tool choice, text, function calls, and usage |
| MCP client | native (transport seam) | `praxo-mcp`; caller supplies a transport program |
| Harmovela sink | native (transport seam) | `praxo-harmovela`; caller supplies a transport program |
| OpenTelemetry sink | native (transport seam) | `praxo-otel`; caller supplies an OTLP/HTTP transport program |
| Subagent delegation | native (synchronous seam) | `praxo-delegation`; synchronous runner callback; no asynchronous manager |
| Retriever | native | `praxo-retriever`; callback seam over query and limit |

## Examples

Runnable examples live under [`language/cobol/examples`](language/cobol/examples).

| Example | What it shows |
| --- | --- |
| [checkpoint](language/cobol/examples/checkpoint) | This example uses the COBOL Core checkpoint allowlist to encode and decode only registered payload types. |
| [event-sink](language/cobol/examples/event-sink) | This example uses the COBOL Core event contract to multicast lifecycle and tool events and filter the tool-only stream. |
| [identity-policy](language/cobol/examples/identity-policy) | This example uses the COBOL Core path policy to allow an in-root action and reject traversal outside the granted root. |
| [mcp](language/cobol/examples/mcp) | This example uses a caller-owned in-process transport with the COBOL MCP client. It covers initialize, `tools/list`, and `tools/call` without a server process. |
| [provider-fallback](language/cobol/examples/provider-fallback) | This example calls a fallback only after the primary fails and preserves the primary failure when both fail. |
| [retry](language/cobol/examples/retry) | This example retries a transient failure with a bounded attempt count and keeps the exhausted failure state. |
| [service](language/cobol/examples/service) | This example defines a transport-neutral request handler boundary with health, principal, and run cases. Wire it into any COBOL HTTP server. |
| [streaming](language/cobol/examples/streaming) | This example accumulates stream chunks and checks that they reconstruct the final output. |
| [structured-output](language/cobol/examples/structured-output) | This example validates a final JSON answer against a schema and rejects invalid output. |

## Verify

Run the checks from `language/cobol`:

```sh
python language/cobol/run-tests.py
```

This mirror contains the language source and the shared `spec/` vectors, so the implementation can be built and tested here. See [`language/cobol/README.md`](language/cobol/README.md) for the exact commands. The monorepo CI runs conformance, API snapshot, and native tests for this implementation.

## Community

- X: <https://x.com/axisvela>
- Weibo: <https://weibo.com/u/1936025761>

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
