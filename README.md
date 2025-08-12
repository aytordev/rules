<div align="center">
<h1>
Agent Rules
</h1>
</div>

# aytordev's Agent Rules Repository

This repository contains the rules and configurations that apply to AI agents across different IDEs to maintain consistency, quality, and best practices in development workflows. The rules are designed to be modular, version-controlled, and easily integrable across various development environments.

This implementation focuses on creating a centralized source of truth for agent behavior, ensuring that AI assistants provide consistent guidance regardless of the IDE or development context being used.

## What are Agent Rules?

Agent Rules are a structured approach to managing AI assistant configurations and behaviors in development environments. They categorize rules into different types:

- **Soft Rules**: Guidelines and preferences that influence agent behavior but allow flexibility. Examples include:
  - Code style preferences
  - Documentation standards
  - Project structure recommendations
  - Communication tone and approach

- **Hard Rules**: Strict requirements that agents must follow without exception. Examples include:
  - Security practices
  - Compliance requirements
  - Critical coding standards
  - Prohibited actions or patterns

This separation allows for better organization and ensures that critical requirements are always enforced while maintaining flexibility for stylistic preferences.

## Repository Structure

```
└── rules/    # Core rule definitions
```

The repository focuses on the `rules/` directory, where you will find all agent rule definitions. You can add, modify, or remove rules within this directory as needed.

### Rule Priorities

All rules must include a numeric `priority` field to indicate their importance. Lower numbers represent higher priority:

- `1`: Critical (must always be enforced)
- `2`: High
- `3`: Medium
- `4`: Low

This allows you to sort and filter rules by importance, and helps both humans and automation tools understand which rules are most critical.

**Example rule definition:**
```yaml
name: "secure-auth"
type: "hard"
priority: 1
description: "Authentication must use secure protocols"
rules:
  - enforce_tls: true
```

## System Requirements

To work with this repository, you need:

- **Git** - Version control
- **YAML/JSON Parser** - Configuration file processing
- **Bash/Zsh** - Automation script execution

## Quick Start

1. **Clone the repository:**
   ```bash
   git clone <repository-url> agent-rules
   cd agent-rules
   ```

2. **Add or modify rules in the `rules/` directory as needed.**

## Contributing

Contributions are welcome! See `CONTRIBUTING.md` for more details.

## Versioning

This repository follows semantic versioning (SemVer) to ensure compatibility and change traceability.
