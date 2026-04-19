# Verifyli

**AI voice agents for automated verification calls.**

🔗 **Live demo:** https://verifyli.vercel.app/

> This is a public-facing overview of Verifyli. The production codebase is private.

---

## What it is

Verifyli automates the most time-consuming step in background screening: the outbound verification phone call. An AI voice agent calls employers, schools, or references, follows a deterministic script, collects structured data, and produces an audit-ready verification record — end to end, hands-off.

Verification calls are highly scripted, highly repetitive, and today they're done one human at a time. Verifyli turns that into a configured agent that runs in parallel, 24/7, with a verbatim audit trail for every call.

## Why it matters

Background screening is a multi-billion dollar industry where the bottleneck is not intelligence — it's call throughput. A trained analyst spends most of their day on hold, leaving voicemails, and re-dialing. The actual script, once someone picks up, is a few minutes of confirm-or-deny questions against known candidate claims.

That's a perfect shape for AI: bounded domain, deterministic flow, structured output, well-understood edge cases.

## What's different about the approach

- **Config-driven, not code-driven.** New verification types (employment, education, references, etc.) are added by writing a YAML file. The runtime is agent-agnostic.
- **Compliance is enforced by the infrastructure, not the prompt.** Critical rules (recorded-line disclosure, never-disclose-requestor, accept-refusal-immediately) live in the orchestration layer where the LLM physically cannot bypass them.
- **Every call is event-sourced.** The audit trail is not a log — it's the source of truth. Call state is reconstructable event by event.
- **AI-native stack end to end.** Voice pipeline, transcription, LLM orchestration, post-call evals, summary generation, and PDF report rendering are all automated.

## Where it's going

Verification calls are the starting point, not the product. The vision is an AI-native compliance platform that spans every modality a background check touches — voice, email, SMS, web portals — and replaces traditional screening infrastructure with something faster, more accurate, more auditable, and dramatically more cost-efficient.

Traditional compliance platforms were built for a world where humans did the work and software tracked the work. Verifyli inverts that: the AI does the work, and humans handle exceptions.

## Tech stack (high level)

Python · async FastAPI · React · TypeScript · Managed voice/telephony pipeline · LLM-backed post-call evals · Event-sourced datastore · Server-side PDF report generation · Railway + Vercel

## About

Built by **Chaitanya Rajkumar** — AI-native product builder. I'm interested in taking long-standing, human-labor-intensive workflows and rebuilding them from scratch with the latest AI primitives. Verifyli is one such workflow: everything a trained analyst does on a verification call, reimagined as a configured agent.

---

© 2026 Chaitanya Rajkumar. All rights reserved.
