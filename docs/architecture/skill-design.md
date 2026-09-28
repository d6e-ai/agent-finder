# Skill design

D6E Agent Finder is a portable instruction-only Skill. Its host AI performs the analysis in its own available context. This repository contains no history collection service, storage layer, D6E API client, or scheduled runtime.

## Flow

1. The host AI states the available-context and abstract-output boundary in one short sentence.
2. It inspects only legitimate, actually available conversation, memory, project, and user-provided context.
3. It groups comparable observed tasks, checks for a repeat signal, and removes one-off or unsafe work.
4. It ranks a small number of specific workflows by automation potential and evidence confidence.
5. It shows a readable diagnosis and a matching JSON Workflow Definition for user review.
6. Sharing with D6E is a separate, explicit user action after a real destination is verified.

## Trust boundaries

The host AI may see raw context under its existing access rules. The readable result and JSON are generalized before they leave that context. The JSON must not contain raw conversation text, prompts, identifiers, credentials, private paths, or confidential figures. A schema validates shape but cannot prove privacy; the host AI must review free-text fields for leakage.

The schema in [workflow-definition.schema.json](../../skills/d6e-agent-finder/references/workflow-definition.schema.json) is version `0.1`. It captures a proposed trigger, current and agent processes, likely connector needs, approval requirement, potential, confidence, and a non-identifying evidence summary. Connector names are requirements to investigate, not promises of product support.

The next product stages may consume this reviewed definition to design Connector, Trigger, AI processing, and Human Approval. This Skill does not claim those stages are implemented.
