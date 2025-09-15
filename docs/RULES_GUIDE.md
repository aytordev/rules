# Agent Rules Guide

*See also: [Project README](../README.md) for repository overview and [CONTRIBUTING.md](../CONTRIBUTING.md) for contribution workflow.*

This guide explains how to create, structure, and maintain `.rules` files for AI IDE integrations. Follow these best practices to ensure your rules are effective, consistent, and compatible across environments.

## What Are `.rules` Files?

`.rules` files define project-specific instructions, coding standards, and context for AI-powered code generation and understanding.

## Anatomy of a Rule

A robust `.rules` file typically includes the following sections:

- **name**: Unique identifier for the rule
- **description**: Brief summary of what the rule enforces
- **filters**: Criteria for targeting files or code (e.g., file extensions, content patterns)
- **actions**: What happens when the rule matches (e.g., suggest improvements, enforce changes)
- **examples**: Before/after code samples to clarify intent
- **metadata**: Priority, version, tags, and other organizational info

For contribution workflow and commit conventions, refer to [CONTRIBUTING.md](../CONTRIBUTING.md).

## Writing Rules

- Use clear, concise language
- Structure rules using YAML for complex logic, JSON for simple cases
- Document the purpose and scope of each rule
- Include actionable suggestions and educational context
- Provide before/after code examples

## Filtering Strategies

Filters allow you to target specific files or code constructs:

- **file_extension**: Apply rules to certain file types (e.g., `.ts`, `.js`)
- **content**: Use regex patterns to match code structures (e.g., classes, interfaces, functions)

Example:
```yaml
filters:
  - type: file_extension
    pattern: "\\.ext$"
  - type: content
    pattern: "someRegexPattern"
```

## Validating Rules

- Test rules in supported IDEs
- Ensure schema compliance
- Check for conflicts with existing rules
- Use sample inputs to verify expected suggestions or enforcement

## Actions

Actions define what happens when a rule matches:

- **suggest**: Provide guidance, best practices, or code improvements
- **enforce**: Require changes or block undesired patterns
- **message**: Use multi-line, markdown-formatted messages for clarity

Example:
```yaml
actions:
  - type: suggest
    message: |
      Please follow the recommended coding guidelines:
      - Keep functions small and focused
      - Use meaningful variable names
      - Avoid duplicated code
```

## Example Rule

### Simple JSON Example

```json
{
  "name": "example-rule",
  "description": "Describe what this rule enforces",
  "severity": "warning",
  "pattern": "somePattern"
}
```

### Generic YAML Example

```yaml
name: generic_rule
description: Enforces a generic coding guideline
filters:
  - type: file_extension
    pattern: "\\.ext$"
  - type: content
    pattern: "someRegexPattern"

actions:
  - type: suggest
    message: |
      Please follow the recommended coding guidelines:
      - Keep functions small and focused
      - Use meaningful variable names
      - Avoid duplicated code

examples:
  - input: |
      # Before: Not following guideline
      def doStuff(x): print(x)
    output: |
      # After: Following guideline
      def print_value(value):
          print(value)
metadata:
  priority: medium
  version: 1.0
  tags:
    - generic
    - best-practices
```

## Best Practices

- Keep rules atomic and focused
- Maintain cross-platform compatibility
- Update documentation for any new or changed rules
- Use metadata for organization and discoverability
- Prefer composition and modularity in rule design


