# Skill design

D6E Agent Finder is a portable instruction-only Skill. Its host AI performs the analysis in its own available context. This repository contains no history collection service, storage layer, D6E API client, or scheduled runtime.

## Flow

1. The host AI states the available-context and abstract-output boundary in one short sentence.
2. It inspects only legitimate, actually available conversation, memory, project, and user-provided context.
3. It groups comparable observed tasks, checks for a repeat signal, and removes one-off or unsafe work.
4. It ranks a small number of specific workflows by automation potential and evidence confidence.
5. It shows a readable diagnosis and a matching JSON Workflow Definition for user review.
6. Sharing with D6E is a separate, explicit user action through an inquiry form in a verified supported locale. The user reviews the exact JSON and contact details before submission.

## Trust boundaries

The host AI may see raw context under its existing access rules. The readable result and JSON are generalized before they leave that context. The JSON must not contain raw conversation text, prompts, identifiers, credentials, private paths, or confidential figures. A schema validates shape but cannot prove privacy; the host AI must review free-text fields for leakage.

The schema in [workflow-definition.schema.json](../../skills/d6e-agent-finder/references/workflow-definition.schema.json) is version `0.1`. It captures a proposed trigger, current and agent processes, likely connector needs, approval requirement, potential, confidence, and a non-identifying evidence summary. Connector names are requirements to investigate, not promises of product support.

The next product stages may consume this reviewed definition to design Connector, Trigger, AI processing, and Human Approval. This Skill does not claim those stages are implemented.

## Inquiry submission

The D6E inquiry form is a contact form, not a Workflow Definition API. The Skill selects a live supported locale using the user's explicit preference or current language, with a disclosed English fallback if no language match exists. The currently verified [English](https://www.d6e.ai/en-US#inquiry) and [Japanese](https://www.d6e.ai/ja-JP#inquiry) forms share the same fields and message limit. Its message field can carry the abstract JSON, while company, contact name, and email are separate user-supplied contact fields. The Skill checks the selected live form before submission, prepares a valid payload within its message limit, and requires approval of the exact outgoing content. If the full JSON does not fit, it presents a clearly reduced candidate set for approval. It does not silently truncate or make multiple submissions.
