# Documented Artifact Taxonomy

## Rationale for Structured Taxonomy
The foundational system requires a **comprehensive yet concise documentation taxonomy** to avoid the common pitfalls of:
- Ad-hoc documentation (incomplete, inconsistent, or missing critical dimensions)
- Siloed information (security details in code comments but not in formal docs)
- Inconsistent metadata (no standard for dates, owners, or validation)

This taxonomy solves these problems by providing a **fixed set of artifact types** that collectively cover all essential project dimensions while preventing information fragmentation.

## Taxonomy Structure and Coverage
The taxonomy is designed to cover all necessary project aspects through 13 core artifact types, organized by **project dimension**:

| Dimension | Core Artifacts | Coverage Purpose |
|-----------|----------------|------------------|
| **Technical Assets** | `languages.md`, `integrations.md`, `architecture.md`, `communication.md` | Captures foundational technology choices, dependencies, and system interactions |
| **Development Lifecycle** | `features.md`, `fixes.md`, `version.md`, `tests.md` | Documents feature progression, defect resolution, release history, and quality assurance |
| **Operational Context** | `project-status.md`, `frontend.md`, `backend.md` | Tracks real-time project health, frontend/backend evolution, and operational dependencies |
| **Security & Compliance** | `security.md` | Centralizes all security controls, audits, and compliance status |
| **Governance & Traceability** | `memory-bank/index-memory-bank.md` | Provides the single-point-of-truth for all artifacts |

*Note: This taxonomy intentionally excludes operational implementation details (e.g., "how to write a bug fix entry")—these are covered in later operational rules.*

## Why This Specific Structure?
1. **Avoids Redundancy**
   Each artifact covers a distinct dimension (e.g., `fixes.md` handles problems while `features.md` handles solutions)

2. **Enforces Completeness**
   The 13 artifacts collectively ensure no critical project aspect is undocumented (e.g., security must have dedicated coverage)

3. **Prevents Over-Engineering**
   The structure includes *only* what's necessary for traceability (e.g., no separate `requirements.md`—covered by `features.md` with requirement links)

4. **Supports Auditability**
   All artifacts have standardized fields (date, owner, reference) enabling automated audit trails

## Cross-Functional Value
This taxonomy serves multiple stakeholders by design:

| Stakeholder | How Taxonomy Supports Them |
|-------------|---------------------------|
| **Developers** | Knows exactly where to find integration details (not buried in code comments) |
| **Security Team** | Has central location for all security controls and audit results |
| **Project Managers** | Can instantly assess project health via `project-status.md` and `version.md` |
| **New Team Members** | Onboards using structured artifact set instead of scattered notes |
| **Compliance Officers** | Validates against `security.md` and `version.md` without digging through code |

## Future-Proofing Through Structure
The taxonomy is designed for scalability:
- **New artifacts** can be added only when a new dimension *cannot* be covered by existing types (e.g., adding `compliance.md` would require proving it's distinct from `security.md`)
- **Field standardization** across all artifacts enables automated metadata extraction (e.g., "last update date" in every file)
- **Dependency mapping** between artifacts is implicit (e.g., `features.md` links to `fixes.md` when a bug blocks a feature)

---

**Why This Taxonomy Matters**
This document is not just a catalog—it establishes the **conceptual bedrock** upon which all operational documentation (e.g., `Memory_Bank_Rule_Dolutech.md`) must align. By defining *what* needs to be documented (not *how*), it ensures:
- All agents produce consistent documentation regardless of implementation
- Documentation remains useful across projects and time
- The system avoids the common trap of "documentation that's incomplete or irrelevant"

This taxonomy makes the memory bank **not merely a document dump**, but a **structured knowledge graph** enabling:
- Cross-referencing (e.g., "What security fixes impact feature X?")
- Predictive analytics (e.g., "Features requiring fixes in last 30 days")
- Automated compliance reporting
