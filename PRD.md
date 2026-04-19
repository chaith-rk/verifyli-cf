# Product Overview

## The problem

Background verification today is throughput-bound. The work that takes longest — calling employers, schools, and references to confirm candidate-provided details — is also the most repetitive and scriptable. Trained analysts spend most of their time on hold, on voicemail, or re-dialing. The actual conversation, once it happens, is a short, structured exchange.

This creates three compounding issues: high labor cost per verification, slow turnaround for the end customer, and a ceiling on how quickly a screening company can scale without hiring.

## The insight

A verification call has three properties that make it an unusually good fit for AI:
1. **Bounded script.** The agent is never improvising — it's confirming known claims.
2. **Structured output.** The call either produces a matched field or a discrepancy.
3. **Well-understood edge cases.** Third-party redirects, limited-policy employers, no-record responses, hostile verifiers — all documented and repeatable.

An AI voice agent that follows a deterministic script, enforces compliance at the infrastructure level, and writes every event to an immutable audit log can match the quality of a trained analyst at a fraction of the per-call cost.

## The product

Verifyli is a voice-AI platform where any verification workflow can be defined as a configuration file. The runtime initiates the call, drives the conversation, records structured data, handles edge cases, and produces a final verification record with a full event history.

## Who it serves

- **Operations teams** — offload routine calls, focus human time on exception cases.
- **Operations leadership** — scale verification volume without scaling headcount linearly.
- **Compliance** — immutable audit trails, enforced disclosure rules, encrypted PII at rest.

## Core product decisions

- **Confirm-or-deny, not open-ended.** The agent never asks open questions. It confirms candidate-provided values. This bounds the LLM's behavior and sharpens output quality.
- **Exact match or review.** Any discrepancy — even a one-day date mismatch — is flagged for human review rather than silently reconciled.
- **Refusal is always accepted immediately.** The agent never pushes back on a hostile or uncooperative verifier.
- **Multi-agent from day one.** The architecture assumes multiple verification types, not just the first one shipped.

## Success criteria

- High completion rate on cooperative calls
- High field-level data accuracy
- 100% compliance on critical disclosure and refusal-handling rules
- Sub-day configuration time for a new agent type

## Vision

Verification calls are the first workflow, not the last. The goal is an AI-native compliance platform that operates across every modality a background check requires — phone, email, message, web portal — orchestrated as one system.

Today's screening industry runs on legacy platforms that were designed around human labor: tickets, queues, case managers, manual data entry. Verifyli is being built as the opposite — AI agents own the execution, humans own the exceptions, and the infrastructure is compliance-first by construction. The outcome is a screening stack that is quicker, more accurate, more compliance-driven, and materially more cost-efficient than anything on the market today.
