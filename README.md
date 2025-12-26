# Suggest Skills

This repository contains the `skill-proposer` skill, which analyzes conversations with AI agents and suggests skill candidates based on **Evaluation-Driven Development (EDD)** principles. The skill helps identify root causes of agent failures and proposes new skills or updates to existing ones.

## What This Skill Does

The `skill-proposer` skill uses a **root cause analysis approach** to identify why AI agents fail, rather than just documenting what went wrong. It focuses on:

- **Identifying friction points**: Places where corrections were needed, multiple exchanges occurred, or incorrect assumptions were made
- **Analyzing root causes (Why)**: Understanding the underlying knowledge gaps that led to failures
- **Proposing solutions**: Suggesting new skills or updates to existing skills that would prevent similar issues

The skill follows the principle that **"Why" analysis is more valuable than "What" documentation** - it identifies missing knowledge (project-specific patterns, domain rules, conventions) that, if provided, would have prevented the issue from occurring.

## About Agent Skills

Agent Skills is a simple, open format for giving agents new capabilities and expertise. Skills are folders containing instructions, scripts, and resources that agents can discover and use.

### What Skills Enable

- **Domain Expertise**: Package specialized knowledge as reusable instructions
- **New Capabilities**: Grant agents new abilities (e.g., presentation creation, MCP server building, dataset analysis)
- **Repeatable Workflows**: Transform multi-step tasks into consistent, auditable workflows
- **Interoperability**: Reuse the same skills across different skill-enabled agent products

## Usage

The skill is automatically invoked with requests such as:
- "suggest skills"
- "skill candidates"
- "analyze improvements"

### Example Usage

Simply ask your agent to analyze a conversation:

```
Analyze this conversation and suggest skill candidates
```

The skill will:
1. Identify friction points in the conversation
2. Analyze root causes (Why didn't the agent know this?)
3. Generate proposals for new skills or updates to existing ones
4. Provide a structured report with prioritized recommendations

### Understanding Root Cause Patterns

The skill uses a catalog of root cause patterns to identify skill candidates. Common patterns include:

- **Lack of Project-Specific Knowledge**: Missing project conventions, tech stack choices, or patterns
- **Lack of Domain Knowledge**: Missing business rules or domain terminology
- **Insufficient Understanding of Type Definitions**: Missing type definitions or schemas
- **Insufficient Understanding of Workflows**: Missing project-specific procedures
- **Lack of Architectural Decision Context**: Missing ADRs or design rationale
- **Lack of Implicit Conventions**: Missing undocumented team practices

For a complete list of patterns, see [`skills/references/patterns.md`](skills/references/patterns.md).

## Prerequisites

Before using the skills in this repository, ensure you have:

- **A skill-enabled AI agent**:
  - Claude Desktop (latest version)
  - Cursor IDE (with skills support)
  - Codex (OpenAI)
  - Or any other agent that supports the Agent Skills format
- **Git** (for cloning the repository)
- **Basic familiarity** with the Agent Skills format (see [Agent Skills Specification](https://agentskills.io/specification))

## Quick Start

Get started with `skill-proposer` in 3 steps:

1. **Clone the repository**
   ```bash
   git clone https://github.com/ryoryo34/skills-proposer.git
   cd skills-proposer
   ```

2. **Configure your agent**
   - **Claude Desktop / Cursor**: Add the repository path to your skills directory in settings
   - **Codex**: Use the `$skill-installer` command to install skills from this repository

3. **Start using**
   - Restart your agent
   - Ask: "Analyze this conversation and suggest skill candidates"
   - Or use trigger phrases: "suggest skills", "skill candidates", "analyze improvements"

## Skill Structure

The `skill-proposer` skill has the following structure:

```
skills/
├── SKILL.md              # Skill description and detailed usage instructions
├── references/           # Reference materials and documentation
│   └── patterns.md       # Catalog of root cause patterns for skill identification
└── scripts/              # Executable scripts (optional)
```

### Key Files

- **`SKILL.md`**: Contains the skill's metadata and detailed instructions for analyzing conversations and generating skill proposals. It includes the analysis process, output format, and best practices.
- **`references/patterns.md`**: Provides a catalog of common root cause patterns that help identify skill candidates. This file is referenced during analysis to categorize friction points and determine appropriate skillification strategies.

## Creating Skills

To create a new skill:

1. Create a new directory within the `skills/` directory
2. Create a `SKILL.md` file with the following format:

```markdown
---
name: skill-name
description: Skill description
---

# Usage

Describe the detailed usage of the skill here.
```

3. Add `references/` or `scripts/` directories as needed

**Tip**: When creating skills based on `skill-proposer` recommendations, refer to [`skills/references/patterns.md`](skills/references/patterns.md) to understand which type of knowledge should be documented and where (e.g., project-specific conventions in `references/`, workflows in `SKILL.md`).

For detailed specifications, see the [Agent Skills Specification](https://agentskills.io/specification).

## Reference Resources

This repository was created with reference to the following resources:

- [Anthropic's Skills Repository](https://github.com/anthropics/skills/tree/main/skills) - Standard specification and sample skills for Agent Skills
- [OpenAI's Skills Repository](https://github.com/openai/skills) - Skills catalog for Codex
- [Agent Skills Homepage](https://agentskills.io/home) - Official documentation for Agent Skills

## Contributing

Contributions for skill improvements and new skills are welcome. Feel free to create Issues or Pull Requests.

## Related Links

- [Agent Skills Specification](https://agentskills.io/specification)
- [Agent Skills Integration Guide](https://agentskills.io/integrate)
- [Anthropic's Skills Repository](https://github.com/anthropics/skills)
- [OpenAI's Skills Repository](https://github.com/openai/skills)
