rules/README.md
```
<div align="center">
<h1>
<img width="100" src="assets/rules-logo.png" /> <br>
</h1>
</div>

# aytordev's AI IDE Rules Reference Repository

This is a curated, reference collection of `.rules` files designed to help you enhance your AI experience across projects and technologies. Inspired by [awesome-cursorrules](https://github.com/PatrickJS/awesome-cursorrules), this repository centralizes best practices, project-level instructions, and context for code generation and understanding—making your IDE smarter and your workflow more consistent.

By defining custom rules, you can tailor AI behavior to your project's needs, improve consistency, and share knowledge with your team.

## What are `.rules` files?

`.rules` files provide repo-specific "Rules for AI"—project-level instructions, best practices, and context for code generation and understanding. They enable you to:

- **Customize AI Behavior**: Tailor AI responses to your project's requirements for more relevant and accurate code suggestions.
- **Enforce Consistency**: Apply coding standards and best practices, ensuring generated code aligns with your style guidelines.
- **Provide Context Awareness**: Supply important context—such as architectural decisions, commonly used methods, or libraries—for more informed code generation.
- **Boost Productivity**: Well-defined rules reduce manual editing and speed up development.
- **Align Teams**: Shared `.rules` files ensure consistent AI assistance for all team members.
- **Share Project-Specific Knowledge**: Include info about structure, dependencies, or unique requirements for more accurate suggestions.

Place a `.rules` file in your project's root directory to unlock these benefits.

## Repository Structure

```
.
├── assets/                         # Logos, images, and documentation resources
│   └── rules-logo.png              # Project logo and branding
│
├── docs/                           # Extended documentation
│   └── RULES_GUIDE.md              # Comprehensive guide to rule authoring
│
├── .rules                          # Contribution guidelines and global rules
├── .gitignore                      # Git ignore rules
├── CONTRIBUTING.md                 # Contribution guidelines
├── LICENSE                         # Project license
└── README.md                       # Project documentation
```

### Key Directories

| Directory      | Purpose |
|----------------|---------|
| `docs/`        | Extended documentation and guides |
| `assets/`      | Logos, images, and non-sensitive resources |

### Important Files

- `.rules`: Global rules and contribution guidelines
- `rules/README.md`: Documentation for available rules and usage
- `docs/RULES_GUIDE.md`: In-depth guide to authoring and customizing rules
- `CONTRIBUTING.md`: How to contribute new rules or improvements
- `LICENSE`: Project license and usage terms

## System Requirements

To use and contribute to this repository, you'll need:

### Core Dependencies
- **Git** - For version control
- **Your IDE** - VSCode, Neovim, JetBrains, etc.

### Recommended Tools
- **AI Service Account** - (e.g., OpenAI, Anthropic, etc.) for advanced integrations
- **Task Runner** - Such as Just, Make, or npm scripts for automation

## Documentation

For detailed information on rule authoring, integration, and best practices, see [docs/RULES_GUIDE.md](docs/RULES_GUIDE.md).

For contribution workflow and commit conventions, see [CONTRIBUTING.md](CONTRIBUTING.md).

## Contributing

Contributions are welcome! To add a new `.rules` file:

1. Fork this repository.
2. Create a new folder in the `rules` directory, following the pattern: `technology-focus-rules-prompt-file`
3. Add your `.rules` file to the new folder.
4. Optionally, include a README.md in the folder for credit and description.
5. Update this README.md, adding your file to the correct category.
6. Ensure your contribution follows the guidelines in the [`.rules`](./.rules) file at the root.
7. Submit a pull request.

Please ensure your contribution is original or properly credited. Refer to the `.rules` file in the root for detailed guidelines.

## License

This project is licensed under the [MIT License](./LICENSE).

## Acknowledgements

This project stands on the shoulders of many talented individuals and open-source projects. Special thanks to:

### Inspirations & Contributors
- **[PatrickJS](https://github.com/PatrickJS)** - For pioneering awesome-cursorrules
- **Open Source Community** - For sharing ideas and tools

### Community
To everyone contributing to smarter developer tools—your work makes this possible.

[Return to top](#aytordevs-ai-ide-rules-reference-repository)
