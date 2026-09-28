# D6E Agent Finder

Find repetitive work you can turn into AI agents.

This repository contains a portable AI Skill at [skills/d6e-agent-finder](skills/d6e-agent-finder/SKILL.md). It analyzes only context that the user's current AI can legitimately inspect, then proposes evidence-backed automation workflows. The shareable JSON contains abstract workflow descriptions, not conversation history.

Copy the skill directory into the skills location supported by your AI client, then invoke `d6e-agent-finder`. After reviewing the Workflow Definition JSON, you can ask the AI to submit it through the [D6E inquiry form](https://www.d6e.ai/ja-JP#inquiry). Submission requires your contact details and final approval.

The behavior and privacy boundary are documented in [docs/architecture/skill-design.md](docs/architecture/skill-design.md).
