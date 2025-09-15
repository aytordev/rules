# Agent Rules Guide

This guide explains how to create, structure, and maintain `.rules` files for AI IDE integrations. Follow these best practices to ensure your rules are effective, consistent, and compatible across environments.

## What Are `.rules` Files?

`.rules` files define project-specific instructions, coding standards, and context for AI-powered code generation and understanding.

## Writing Rules

- Use clear, concise language
- Follow the defined JSON schema for rules
- Include examples where possible
- Document the purpose and scope of each rule

## Validating Rules

- Test rules in supported IDEs
- Ensure schema compliance
- Check for conflicts with existing rules

## Best Practices

- Keep rules atomic and focused
- Maintain cross-platform compatibility
- Update documentation for any new or changed rules

## Example Rule

```json
{
  "name": "no-console-log",
  "description": "Disallow use of console.log in production code",
  "severity": "error",
  "pattern": "console\\.log"
}
```
