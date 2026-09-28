# D6E Agent Finder

Find repetitive work you can turn into AI agents.

This repository contains a portable AI Skill at [skills/d6e-agent-finder](skills/d6e-agent-finder/SKILL.md). It analyzes only context that the user's current AI can legitimately inspect, then proposes evidence-backed automation workflows. The shareable JSON contains abstract workflow descriptions; the Skill does not transmit conversation history or send data to D6E.

Copy the skill directory into the skills location supported by your AI client, then invoke `d6e-agent-finder`. Review its Workflow Definition JSON before sharing it with any service.

The behavior and privacy boundary are documented in [docs/architecture/skill-design.md](docs/architecture/skill-design.md).
