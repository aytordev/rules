# 🤖 Contributing to Agent Rules Repository

This guide outlines the workflow for managing and updating the agent rules repository. Contributors must follow best practices to ensure consistency and quality across all IDE integrations.

## 📋 Table of Contents

- [Guidelines](#-guidelines)
- [Workflow](#-workflow)
  - [1. Branching Strategy](#1-branching-strategy)
  - [2. Making Changes](#2-making-changes)
  - [3. Committing Changes](#3-committing-changes)
  - [4. Review Process](#4-review-process)
  - [5. Merging Changes](#5-merging-changes)
- [Rule Development](#-rule-development)
- [Best Practices](#-best-practices)
- [Tools](#-tools)
- [Example Workflow](#-example-workflow)
- [Code Review Guidelines](#-code-review-guidelines)

## 🔒 Guidelines

1. **Follow rule schemas** - All rules must conform to the defined JSON schemas
2. **Test thoroughly** - Validate rules across different IDEs and scenarios
3. **Document everything** - Provide clear documentation for all new rules
4. **Maintain consistency** - Ensure rules work harmoniously across platforms
5. **Version carefully** - Follow semantic versioning for all changes

## 🔄 Workflow

### 1. Branching Strategy

- Create feature branches from `main`
- Use descriptive branch names with prefixes:
  - `feat/` for new rules or features
  - `fix/` for bug fixes or rule corrections
  - `docs/` for documentation updates
  - `chore/` for maintenance tasks
  - `ide/` for IDE-specific implementations

### 2. Making Changes

1. Pull the latest changes from main
2. Create a new branch for your changes
3. Make atomic, focused changes
4. Test your changes across relevant IDEs
5. Validate rule syntax and schemas

### 3. Committing Changes

Follow the Conventional Commits specification with Gitmoji for consistent and meaningful commit messages.

#### Commit Message Format

```
:emoji_code: type(scope): concise description

[optional body]

[optional footer]
```

#### Gitmoji Reference

| Emoji | Code                  | Description                                     |
|-------|-----------------------|------------------------------------------------|
| 🐛    | `:bug:`              | Fix a bug                                      |
| ✨    | `:sparkles:`         | Introduce new features                        |
| 🔧    | `:wrench:`           | Add or update configuration                   |
| ♻️    | `:recycle:`          | Refactor code                                 |
| 📝    | `:memo:`             | Add or update documentation                   |
| 🚀    | `:rocket:`           | Deploy stuff or improve performance           |
| 🚧    | `:construction:`     | Work in progress                              |
| 🚨    | `:rotating_light:`   | Fix compiler/linter warnings                  |
| 🎨    | `:art:`              | Improve structure/format of the code          |
| ⚡️    | `:zap:`              | Improve performance                           |
| 🔥    | `:fire:`             | Remove code or files                          |
| 🚑    | `:ambulance:`        | Critical hotfix                               |
| 🍱    | `:bento:`            | Add or update assets                          |
| 🚸    | `:children_crossing:`| Improve user experience/usability             |
| 💄    | `:lipstick:`         | Add or update the UI and style files          |
| 🚚    | `:truck:`            | Move or rename files                          |
| 🤖    | `:robot:`            | Add or update AI/agent rules                  |
| 🧠    | `:brain:`            | Add intelligence or logic improvements        |

#### Commit Types

- `feat`: A new rule or feature
- `fix`: A bug fix or rule correction
- `docs`: Documentation only changes
- `style`: Changes that do not affect rule meaning (formatting, etc)
- `refactor`: A rule change that neither fixes a bug nor adds a feature
- `perf`: A change that improves agent performance
- `test`: Adding missing tests or correcting existing tests
- `chore`: Changes to the build process or auxiliary tools

#### Examples

```
:robot: feat(vscode): add typescript formatting rules

- Add consistent TypeScript formatting guidelines
- Configure auto-import organization
- Set up bracket spacing preferences

Closes #123
```

```
:bug: fix(general): correct security rule validation

- Fix regex pattern for password validation
- Update SQL injection prevention rules
- Add missing escape character handling

Closes #456
```

#### Best Practices

1. **Subject Line**
   - Use the imperative mood ("add" not "added" or "adds")
   - First letter lowercase
   - No period at the end
   - Keep it under 50 characters

2. **Body**
   - Explain what and why, not how
   - Use bullet points for multiple changes
   - Wrap at 72 characters

3. **Footer**
   - Reference issues with `Closes #123` or `Fixes #456`
   - Document breaking changes with `BREAKING CHANGE:`
   - Include any relevant migration notes

### 4. Review Process

1. Push your branch and create a merge request
2. Request review from at least one team member
3. Ensure all validation checks pass
4. Address all review comments
5. Test rules in target IDE environments

### 5. Merging Changes

- Squash and merge with a clear, descriptive message
- Delete the feature branch after merge
- Verify all rules validate correctly in main
- Update version number if needed

## 🤖 Rule Development

### Rule Categories

1. **Soft Rules** - Flexible guidelines that can be overridden
2. **Hard Rules** - Strict requirements that must be enforced
3. **Context Rules** - Rules that apply in specific situations
4. **Global Rules** - Rules that apply across all contexts

### Rule Structure

All rules must follow the defined schema:

```yaml
name: "rule-name"
type: "soft" | "hard"
category: "coding-standards" | "security" | "documentation" | "performance"
description: "Clear description of what the rule does"
applies_to: ["language1", "language2"]
ide_specific:
  vscode:
    enabled: true
    settings: {}
  cursor:
    enabled: true
    settings: {}
rules:
  - condition: "description"
    action: "what to do"
    severity: "error" | "warning" | "info"
```

### IDE Integration

When adding IDE-specific rules:

1. Create appropriate directory structure under `rules/`
2. Test integration with the target IDE
3. Document any special configuration requirements
4. Provide installation and setup instructions

## 🏆 Best Practices

- **Atomic changes** - Keep changes small and focused on a single improvement
- **Clear documentation** - Document any new or updated rules thoroughly
- **Cross-platform testing** - Test rules across different operating systems and IDEs
- **Performance consideration** - Ensure rules don't significantly impact IDE performance
- **User experience** - Consider how rules affect developer workflow and productivity

## 🛠️ Tools

### Development Setup

1. **Pre-commit Hooks**
   - Validate rule syntax and schemas
   - Ensure commit messages follow the required format
   - Run automated tests on rule changes

2. **CI/CD Integration**
   - Verify rule validation in all PRs
   - Run integration tests with supported IDEs
   - Automate rule deployment and distribution

3. **Validation Tools**
   - JSON Schema validators for rule structure
   - YAML linters for syntax checking
   - Custom validation scripts for logic verification

## 🔄 Example Workflow

### Adding a New Rule

1. Create a new branch:
   ```bash
   git checkout -b feat/add-logging-standards
   ```

2. Create the rule file following the schema:
   ```bash
   # Edit rules/general/logging-standards.yaml
   ```

3. Add tests and documentation:
   ```bash
   # Create tests/unit/logging-standards.test.js
   # Update docs/RULES.md
   ```

4. Commit the changes:
   ```bash
   git add .
   git commit -m ":robot: feat(general): add structured logging standards"
   ```

5. Push and create a merge request:
   ```bash
   git push -u origin feat/add-logging-standards
   ```

### Adding IDE Support

1. Create a new branch:
   ```bash
   git checkout -b ide/add-webstorm-support
   ```

2. Create IDE-specific directory and rules:
   ```bash
   mkdir -p rules/webstorm
   # Create rule files for WebStorm
   ```

3. Update integration scripts:
   ```bash
   # Update scripts/install.sh
   # Update scripts/sync.sh
   ```

4. Document the integration:
   ```bash
   git add .
   git commit -m ":sparkles: feat(webstorm): add WebStorm IDE support"
   ```

## 🔍 Code Review Guidelines

1. **Rule Quality**
   - Verify rule logic is correct and complete
   - Check for potential conflicts with existing rules
   - Ensure proper categorization and tagging

2. **Documentation**
   - Verify all changes are properly documented
   - Check for clear and comprehensive descriptions
   - Ensure examples are provided where appropriate

3. **Testing**
   - Verify adequate test coverage for new rules
   - Check that integration tests pass
   - Ensure rules work across target platforms

4. **Performance**
   - Review impact on IDE performance
   - Check for efficient rule evaluation
   - Ensure minimal resource usage

## 🚨 Issue Response

1. **Bug Reports**
   - Reproduce the issue in the affected environment
   - Identify root cause and impact scope
   - Provide hotfix if critical, otherwise plan for next release

2. **Feature Requests**
   - Evaluate feasibility and alignment with project goals
   - Discuss implementation approach with team
   - Create detailed specification before implementation

3. **IDE Compatibility**
   - Test across different IDE versions
   - Document any version-specific requirements
   - Provide fallback options where possible

## 📌 Quality Standards

### Rule Development
- All rules must have clear, actionable descriptions
- Rules should be testable and verifiable
- Documentation must include usage examples
- Breaking changes require major version bump

### Code Quality
- Follow established coding standards for configuration files
- Use consistent naming conventions across all rules
- Maintain backward compatibility when possible
- Include comprehensive error handling

### Testing
- Unit tests for individual rules
- Integration tests for IDE compatibility
- Performance tests for rule evaluation
- User acceptance testing with real workflows

## 🤝 Getting Help

For any questions or issues:
1. First, check the README and documentation in `docs/`
2. Search existing issues and discussions
3. For rule-specific questions, consult the relevant IDE documentation
4. Open a new issue with detailed information and reproduction steps

We are committed to fostering a welcoming and inclusive community. Please review our [Code of Conduct](CODE_OF_CONDUCT.md) for expected behavior and reporting procedures.

### Recognition

All contributors are recognized in our [Contributors](CONTRIBUTORS.md) file. Your contributions to improving AI agent behavior across development environments are greatly appreciated!

---

📝 *This document was last updated on December 2024*

💡 *Need help? [Open an issue](https://github.com/aytordev/agent-rules/issues/new/choose) or join our [discussions](https://github.com/aytordev/agent-rules/discussions) for support.*
