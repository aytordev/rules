# Foundational System Overview

## System Objectives
The primary purpose of this framework is to establish a **structured, transparent, and auditable workflow** for AI-powered development agents. This framework ensures:
- **Clarity in agent operations** through mandatory planning-execution separation
- **Full traceability** of all decisions and changes via the memory bank system
- **Safety through explicit user approval** before any code or documentation modification
- **Consistency across projects** by embedding documented principles into the agent's core behavior

## Scope and Intended Audience
- **Scope**: Defines the foundational operating principles for AI agents (not operational implementation details)
- **Intended Audience**:
  - AI agent developers creating new tools
  - Technical leads managing AI-assisted development
  - Security/compliance teams verifying agent behavior
  - Project managers requiring audit trails

## Architectural Vision
The system operates on two core pillars:
1. **Planning-Execution Separation**
   Agents must generate and obtain explicit approval for all work plans before implementation.
2. **Memory Bank Integration**
   All project artifacts (decisions, features, fixes, integrations) are documented in version-controlled memory bank files.

This creates a **single source of truth** that eliminates ambiguity in agent behavior and provides full auditability.

## Guiding Principles
| Principle | Application in Agent Workflow |
|-----------|-------------------------------|
| **Transparency** | Every task breakdown, approach, and outcome is explicitly documented |
| **Traceability** | All changes are recorded in memory bank with timestamps/responsibility |
| **Safety** | Zero execution without user approval ("approval-driven" workflow) |
| **Consistency** | Standardized documentation structure across all projects |
| **Adaptability** | Principles work across programming languages and IDEs |

## Key Terminology
- **Memory Bank**: Central repository for all project documentation (created in `/memory-bank` at project root)
- **Planning Mode**: Agent's phase where tasks are decomposed, explained, and proposed
- **Execution Mode**: Agent's phase where approved tasks are implemented
- **Approval Flow**: Mandatory user validation step before execution begins
- **Foundational Documentation**: High-level principles (this document) enabling operational rules

## Initial Assumptions
1. All projects use Git for version control with standard commit practices
2. AI agents integrate with common IDEs (VSCode, Cursor, etc.)
3. Users are technical stakeholders capable of reviewing implementation plans
4. Documentation requires precise dating and attribution

## Constraints
- **No Implementation Details**: Document defines *why* and *what*, not *how* (to be covered in operational rules)
- **Language-Agnostic**: Principles apply equally to Python, JavaScript, or any technology stack
- **Tool-Agnostic**: Designed for compatibility with all major AI development platforms

---

**Why This Matters**
This document establishes the **non-negotiable foundation** upon which all subsequent agent behavior and operational rules will be built. Without these principles, agents would operate as black boxes—making audits impossible and introducing uncontrolled risk. This foundation ensures every AI-assisted development decision is:
1. Visible before execution
2. Documented for traceability
3. Approved by human stakeholders

It directly enables the memory bank system described in `Memory_Bank_Rule_Dolutech.md` and the planning-execution workflow in `Tasks_and_Planning_Rule_Dolutech.md` by providing the conceptual framework they operationalize.
