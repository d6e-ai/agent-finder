# ADR 2026-09-28: Use the D6E inquiry form for approved diagnoses

## Status

Accepted for the initial Skill.

## Context

The user supplied `https://www.d6e.ai/ja-JP#inquiry` as the place to post a diagnosis and then required support for other locales. The verified `en-US` and `ja-JP` pages each have a contact form with required company, contact name, email, and message fields. The message field has a 5,000-character limit. These are not dedicated JSON ingestion endpoints.

## Decision

The Skill offers a verified localized inquiry form as an optional handoff after showing the readable diagnosis and Workflow Definition JSON. It honors an explicit locale choice, otherwise matches the user's language; if none is supported, it discloses an English fallback. It verifies a locale's form before linking or posting, rather than constructing unverified paths. For a requested submission, it prepares the exact abstract JSON as the message, obtains contact details directly from the user, rechecks live form constraints, and asks for final approval before submitting once. If the full JSON does not fit, it proposes a valid reduced candidate set and discloses the omission. It never sends conversation text or silently truncates the payload.

## Consequences

- Contact details are sent to D6E as form fields, separately from the Workflow Definition.
- A host AI without form interaction can prepare a ready-to-paste message and link, but cannot claim it submitted anything.
- A successful form submission is an inquiry, not proof that an Agent Builder processed the JSON.
