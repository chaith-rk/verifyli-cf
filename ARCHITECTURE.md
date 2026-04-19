# Architecture Overview

A high-level look at how Verifyli is structured. Implementation specifics are intentionally omitted.

## Design principles

**1. The runtime is agent-agnostic.**
There is no "employment verification" code path. There is one generic runtime that executes whatever agent is described in configuration. Adding a new verification type is a config change, not a code change.

**2. Compliance lives below the LLM.**
Prompt-based compliance ("please remember to disclose X") is fragile. Verifyli treats critical rules as infrastructure: the orchestration layer blocks progression until required actions are observed. The LLM cannot route around them.

**3. Every call is a stream of immutable events.**
Call state is derived, not stored. This gives a tamper-evident audit trail for free and makes replay, debugging, and post-call analysis straightforward.

**4. The voice layer is thin.**
We let a managed voice platform handle the hard parts of telephony, STT, and TTS. Our system owns what the agent *knows*, what it *can do*, and what it *records*.

## Logical layers

- **Configuration** — declarative definitions of agent behavior, fields to collect, compliance checkpoints, and voice settings. Validated at load time.
- **Runtime orchestration** — a generic engine that drives the conversation, enforces checkpoints, and records structured data.
- **Persistence** — event-sourced store with per-field encryption for sensitive data.
- **Post-call pipeline** — evaluation, summary generation, and audit-ready report rendering.
- **API + real-time layer** — REST for operator actions, WebSocket for live call observation.
- **Security middleware** — webhook authentication, PII redaction in logs, API authentication, rate limiting.

## Data handling

Sensitive fields are classified at config time and encrypted at rest accordingly. PII never reaches application logs (redaction happens at the log layer). Errors returned to API consumers are always generic.

## Scaling path

The backend is stateless and async. Scaling from pilot volume to production volume is an infrastructure change (container count, managed datastore, caching layer) rather than a code change.
