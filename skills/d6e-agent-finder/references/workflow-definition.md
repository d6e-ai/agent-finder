# Workflow Definition contract

The diagnosis is an idea for an agent, not an instruction to execute it. The readable list and the JSON describe the same ranked candidates. The JSON contains only abstract business process information that the user can review before sharing with D6E.

The machine-readable contract is [workflow-definition.schema.json](workflow-definition.schema.json). Emit a complete JSON object in one fenced `json` block. Do not wrap it in Markdown inside the block, add comments, or include a submission URL.

## Top level

| Field | Meaning |
| --- | --- |
| `skill` | Always `d6e-agent-finder`. |
| `version` | Always `0.1` for this contract. |
| `analysis_scope.description` | Short account of only the source types actually inspected. Do not include source topics or contents. Never imply access to uninspected history. |
| `analysis_scope.limitations` | Specific unavailable or uninspected source types and coverage gaps, without describing the subject matter of excluded requests. Use an empty array if none is known. |
| `workflow_candidates` | Ranked, deduplicated list of 0 to 10 eligible workflows. Do not add filler to reach 3. |

## Candidate fields

| Field | Meaning |
| --- | --- |
| `name` | Short generic workflow name, with no person or customer identifiers. |
| `description` | One sentence describing the recurring business task in abstract terms. |
| `category` | A broad label such as `communication`, `research`, `reporting`, `document_processing`, `data_transfer`, `monitoring`, or `evaluation`. |
| `frequency` | `recurring`, `occasional`, or `unknown`. Do not convert weak signals into invented schedules. |
| `current_process` | Generalized steps the person currently takes, using only supported details. |
| `possible_agent_process` | Plausible trigger, retrieval, AI work, output, and review steps. Treat these as a proposal. |
| `apps` | Likely named services or generic service types. Empty if the source gives no basis. |
| `required_connectors` | Lowercase service or connector-kind identifiers such as `gmail`, `google_drive`, or `email`. These are desired capabilities, not a claim that D6E already offers them. Empty if unknown. |
| `trigger_type` | Primary proposed trigger: `scheduled`, `event_driven`, `manual`, or `unknown`. This can be a proposal even when the current task has no trigger. |
| `human_review_required` | Whether the proposed process must pause for a human before its consequential action. |
| `automation_potential` | `high`, `medium`, or `low`, based on repeatability, stable input and output, feasible automation, and expected value. |
| `confidence` | `high`, `medium`, or `low`, based on inspected evidence for repetition and process detail. Independent of potential. |
| `estimated_benefit` | Qualitative reduction in work or improvement in timeliness. Never invent hours, cost, or volume. |
| `evidence_summary` | Short abstract reason for judging the work repeated, plus any important uncertainty. No raw quotes, record IDs, names, exact subjects, or private paths. |

When `human_review_required` is true, name the specific decision in the readable result and include an approval step in `possible_agent_process`. When false, the readable result should say what oversight remains, such as checking the initial setup or reviewing exceptions. Leave an unsupported service unspecified rather than selecting a fashionable provider.

If there are no qualified candidates, keep `workflow_candidates` empty and restrict the rest of the JSON to source types and coverage limits. Explain missing repeat evidence to the user outside the JSON without restating private one-off topics.
