# ADR 2026-09-28: Analyze in the user's existing AI context

## Status

Accepted for the initial Skill.

## Context

Discovering useful agents requires recognizing repeated work from conversation and project context. Centralizing raw histories in D6E would create unnecessary collection and retention. A host AI can already reason over whatever context its user has made available to it, but access differs by provider and session.

## Decision

The host AI identifies workflow candidates locally and reports its actual analysis scope. It exports only generalized Workflow Definitions for user review. No transcript ingestion, automatic D6E submission, or invented access to past conversations is part of the Skill. Candidates need a repeat signal; fewer than three results are valid when evidence is limited.

## Consequences

- Candidate quality varies with the host AI's genuinely accessible context, and the Skill must disclose limitations.
- A user can inspect and withhold the JSON before sharing it.
- The JSON schema verifies structure but privacy still requires reviewing natural-language fields.
- D6E can later build a receiving and Agent Builder flow without changing this initial collection boundary.
