# Memory Bank Rules – Standard for AI Agents in Software Projects

## Purpose of the Memory Bank

The objective of the memory bank is to ensure that all technical information, decisions, learnings, integrations, and project evolutions are documented, organized, and versioned from the very beginning of development. This facilitates audits, team continuity, onboarding, traceability, governance, and security analysis, providing a single source of reference and consultation throughout the project lifecycle.

## Initial Procedure – How the Agent Should Act

1. **When starting any new project, create a folder in the root called** `memory-bank` **(no name variations).**
2. All files created inside this folder must be in Markdown format (`.md`) and follow the standards and examples established in this document.
3. Each file has a specific purpose and must be updated whenever an event, change, decision, or relevant evolution occurs in the project.
4. The agent must ensure that files are always up to date and consistent, avoiding outdated or duplicated information.
5. The memory bank must be treated as an integral part of project version control (git, svn, etc), receiving commits alongside the source code.

---

## Memory Bank File Structure

### 1. `languages.md`

**Purpose:**

- Document in detail all languages, frameworks, libraries, SDKs, runtimes, build tools, and technology standards adopted in the project.
- Indicate the purpose of each technology (example: "React – frontend SPA", "Prisma – Node.js ORM for PostgreSQL").

**Required content:**

- Name of language/framework/tool
- Version used (always specify)
- Purpose in the project
- Observed advantages and possible limitations
- Last updated date and responsible person

**Validation Requirements:**
- All entries must include version numbers
- Purpose field cannot be empty
- Update date must be within last 30 days for active projects

**Example:**

```
Last Updated: 2024-01-15 | Updated by: John Doe

- Node.js v20.3.0 – Main backend (REST API)
- PostgreSQL v15 – Relational database
- Prisma v5.0 – ORM for Node.js/PostgreSQL integration
- TailwindCSS v3.4 – Frontend styling
- React v18 – Frontend SPA
- Express v4.18 – Backend framework
- Docker v26.0 – Environment orchestration
```

---

### 2. `integrations.md`

**Purpose:**

- List and describe in detail all external integrations (APIs, payment gateways, third-party services, cloud providers, social authentication, webhooks, etc).
- Describe endpoints, methods, authentication, callbacks, scopes, permissions, and sensitive data involved.

**Required content:**

- Name of the integration and provider
- Description of the purpose
- Technical details (endpoint, methods, payloads, authentication, callbacks)
- Critical security/privacy points
- Status (active, deprecated, test, staging)
- Last updated date and responsible person

**Validation Requirements:**
- Security assessment status must be documented
- All active integrations must have recent review date (< 90 days)
- Authentication methods must be explicitly specified

**Example:**

```
Last Updated: 2024-01-15 | Updated by: Security Team

- PagSeguro API (https://api.pagseguro.com) – Payment processing. OAuth2 authentication. Endpoints: /v1/payment, /v1/checkout. Status callbacks at /webhook/pagseguro. Security Review: 2024-01-10. Status: active.
- AWS S3 – File storage. Access via AWS SDK, use of segregated buckets. Minimum permissions applied via IAM. Security Review: 2024-01-05. Status: staging.
- Google OAuth – Social login, OAuth2 authorization, frontend/backend integration, scopes: email, profile. Security Review: 2024-01-12. Status: active.
```

---

### 3. `features.md`

**Purpose:**

- Document each system feature, including business context, implemented rules, involved APIs, start/completion dates, owner, status, and relationship with requirements or tasks (e.g., link to issue in Jira or GitHub).

**Required content:**

- Name of the feature
- Description/summary
- Start and end dates
- Status (in development, completed, reviewed, approved, deprecated)
- Main responsible person
- Relationship with task/requirement
- Involved components and modules
- Last updated date

**Validation Requirements:**
- All features must have assigned responsible person
- Status must be one of predefined values
- Completion date required for completed features

**Example:**

```
Last Updated: 2024-01-15 | Updated by: Ana Costa

- User registration: Allows new users to create an account via email/password. Start: 2024-01-13. Completion: 2024-01-14. Status: completed. Responsible: Ana Costa. Issue: #12. Components: Frontend (React), Backend (Express), Database (PostgreSQL).
- Password recovery: Reset process via token sent by email. Start: 2024-01-15. Status: in development. Responsible: Rafael Lima. Issue: #19. Integration with SendGrid.
```

---

### 4. `fixes.md`

**Purpose:**

- Register in detail found bugs, detected vulnerabilities, security flaws, performance improvements, and any type of correction, indicating impact, date, commit, responsible, and post-fix verification.

**Required content:**

- Clear description of the problem
- Date of identification
- Date of correction
- Reference to commit/pull request
- Person responsible for the fix
- Test/validation performed
- Impact on the system (affects production? requires rollback? is there a workaround?)
- Severity level (Low/Medium/High/Critical)

**Validation Requirements:**
- All fixes must reference specific commits/PRs
- Validation method must be documented
- Critical fixes require post-fix security review

**Example:**

```
Last Updated: 2024-01-15 | Updated by: Pedro Soares

- Bug: 500 error when registering user with already registered email. Identified: 2024-01-15. Fixed: 2024-01-15. Commit: #c2a34b. Responsible: Pedro Soares. Validation: Automated test. Impact: blocked registration, did not affect production. Severity: Medium.
- Vulnerability: CSRF flaw in endpoint /api/user/update. Identified: 2024-01-16. Fixed: 2024-01-17. Commit: #e22ac0. Responsible: Lucas M. Validation: Manual testing + security review. Severity: High.
```

---

### 5. `project-status.md`

**Purpose:**

- Summarize the overall project status: current version, milestones, module status, main risks, next steps, technical pending issues, production/staging environment, and infrastructure health.

**Required content:**

- Current project version
- Last relevant commit and date
- Completed/in-progress modules
- Main pending items or risks
- Production/staging status
- Relevant general notes
- Health indicators (green/yellow/red)

**Validation Requirements:**
- Must be updated at least weekly for active projects
- Health indicators must be justified
- Risk assessment required for yellow/red status

**Example:**

```
Last Updated: 2024-01-17 | Updated by: Project Manager

Version: 1.2.1
Last update: 2024-01-17 (commit #da23b2)
Health Status: Green
Frontend: Completed ✅
Backend: Completed ✅
PagSeguro Integration: In staging review 🟡
Pending: Redis cache adjustment in production
Risks: None currently identified
Next Milestone: v1.3.0 (2024-01-30)
```

---

### 6. `frontend.md`

**Purpose:**

- Document the entire frontend evolution: architectural decisions, routes, components, state patterns, tests, responsiveness strategies, backend communication, SDK integrations, error handling, accessibility, UX standards, optimizations.

**Required content:**

- Decisions made (with justification)
- Folder structure, main components created/changed
- Technologies/tools used (e.g., Redux, Context API, Zustand)
- Direct integrations (APIs, SDKs)
- Implemented authentication and authorization patterns
- Responsiveness, internationalization, accessibility approach
- Build and deployment strategies
- Performance metrics and optimization notes

**Validation Requirements:**
- Architectural decisions must include rationale
- Performance metrics should be quantified when possible
- Accessibility compliance level must be specified

**Example:**

```
Last Updated: 2024-01-15 | Updated by: Frontend Team

Architectural Decisions:
- Adopted React Context for authentication management. Rationale: simplifies the global user flow, reduces bundle size vs Redux.
- All forms use Yup validation and global error handling. Rationale: consistent UX and centralized validation logic.

Technical Implementation:
- Adaptive layout with Tailwind, breakpoints documented in /src/styles/theme.js
- Auth API consumption via axios, using interceptors for token refresh
- Protected pages with HOC AuthGuard
- Performance: Bundle size < 500KB, First Contentful Paint < 2s
- Accessibility: WCAG 2.1 AA compliant
```

---

### 7. `backend.md`

**Purpose:**

- Detail the entire backend structure: architecture, endpoints, authentication/authorization flows, data models, background routines, integrations, workers, queues, cache, logging mechanisms, middlewares, and security standards.

**Required content:**

- Description and diagram of main backend modules
- Implemented endpoints (with methods, payload, business rules)
- Authentication/authorization strategies (JWT, OAuth2, RBAC, ACL)
- Database, cache, queues, jobs integration
- Logging and monitoring policies
- Security controls: validation, sanitization, permissions
- Automated tests (coverage, tools)
- Performance metrics and scaling considerations

**Validation Requirements:**
- API documentation must be current and complete
- Security controls must reference framework standards
- Test coverage percentage must be specified

**Example:**

```
Last Updated: 2024-01-15 | Updated by: Backend Team

Architecture Overview:
- Layered architecture: Controllers → Services → Repositories → Database
- Endpoint POST /api/auth/login – JWT authentication, credential validation by AuthService, logs in Elastic
- Authentication: JWT with 24h expiration, refresh token rotation
- Authorization: RBAC with user roles (admin, user, moderator)

Technical Implementation:
- Prisma ORM for PostgreSQL manipulation, versioned migrations, documented seeds
- Asynchronous job processing using BullMQ and Redis
- Rate limiting: express-rate-limit on all endpoints (100 req/min)
- Test Coverage: 87% (Jest + Supertest)
- Performance: 95th percentile response time < 200ms
```

---

### 8. `architecture.md`

**Purpose:**

- Map the overall project architecture, including textual or visual diagrams, module detailing, main flows, system dependencies, integration points, gateways, middlewares, authentication flows, error control, orchestration, and monitoring.

**Required content:**

- Diagram or textual flow description
- Main components/modules and their communication
- External integration points
- Authentication/authorization flow (frontend, backend, third-party)
- Monitoring, logging, alarm structure
- Resilience patterns (retry, fallback, circuit breaker, etc)
- Scalability considerations and bottlenecks

**Validation Requirements:**
- Architecture diagrams must be kept current with implementation
- Integration points must be documented in detail
- Scalability limits must be quantified

**Example:**

```
Last Updated: 2024-01-15 | Updated by: Tech Lead

System Architecture:
[Frontend (React)] <-> [API Gateway (Express)] <-> [Services (Auth, Payments, User)] <-> [Database (PostgreSQL)]
                                |
                         [Background Jobs (Redis + BullMQ)]
                                |
                         [External Services (Email, Payment Gateway)]

Integration Points:
- Auth service communicates with external email service via worker queue
- Payment integration protected by application firewall (WAF)
- All external calls use circuit breaker pattern (3 failures = 30s cooldown)

Monitoring Stack:
- Application: Prometheus + Grafana
- Logs: ELK Stack (Elasticsearch, Logstash, Kibana)
- Alerts: PagerDuty integration for critical issues

Scalability Limits:
- Database: Up to 1M users before sharding required
- API: Horizontally scalable, load balancer configured
- Background jobs: Auto-scaling based on queue depth
```

---

### 9. `communication.md`

**Purpose:**

- Document in detail how the frontend communicates with the backend and other services, protocols used, exposed endpoints, API contracts, request/response examples, authentication formats, and message standards.

**Required content:**

- Endpoints and routes consumed by frontend
- HTTP methods, payloads, required headers
- Protocols (REST, GraphQL, WebSocket, etc)
- Authentication patterns used in communications
- Real examples of requests and responses (with payloads)
- Error handling and retry strategies
- API versioning strategy

**Validation Requirements:**
- All endpoints must be documented with examples
- Authentication flows must be detailed
- Error responses must be standardized

**Example:**

```
Last Updated: 2024-01-15 | Updated by: API Team

API Communication Patterns:

Authentication Flow:
POST /api/auth/login
Request: { "email": "user@example.com", "password": "securepass" }
Response: { "token": "jwt_token_here", "user": { "id": 1, "email": "user@example.com" } }
Headers: Authorization: Bearer {token} for protected routes

Data Endpoints:
GET /api/users/profile (Protected)
Headers: Authorization: Bearer {token}
Response: { "id": 1, "email": "user@example.com", "profile": {...} }

Real-time Communication:
- WebSocket connection for live notifications at ws://api.example.com/notifications
- Heartbeat every 30 seconds to maintain connection
- Automatic reconnection with exponential backoff

Error Handling:
- Standard HTTP status codes
- Consistent error format: { "error": "message", "code": "ERROR_CODE", "details": {...} }
- Client-side retry for 5xx errors (3 attempts with exponential backoff)
```

---

### 10. `version.md`

**Purpose:**

- Maintain a detailed history of project versions, release dates, changes, main features, bugfixes, status, and delivery environment (production/staging/dev).

**Required content:**

- Version number/ID (following semantic versioning)
- Release date
- Main changes (feature/fix/breaking change)
- Status (production, staging, dev)
- Migration notes (if applicable)
- Performance impact assessment

**Validation Requirements:**
- Must follow semantic versioning (MAJOR.MINOR.PATCH)
- Breaking changes must be clearly documented
- Production releases require approval documentation

**Example:**

```
Last Updated: 2024-01-17 | Updated by: Release Manager

v1.2.1 (2024-01-17)
Status: Production
Changes: 
- Fix: CSRF vulnerability in user update endpoint
- Performance: Optimized database queries (20% improvement)
Migration: None required
Approval: Security team approved 2024-01-17

v1.2.0 (2024-01-15)
Status: Production  
Changes:
- Feature: Password recovery system
- Feature: Email notifications
- Breaking: Updated API response format for /api/users
Migration: Frontend requires update to handle new API format
Approval: Product team approved 2024-01-14

v1.1.0 (2024-01-10)
Status: Deprecated
Changes: 
- Feature: User registration system
- Feature: Basic authentication
- Fix: Input validation improvements
Migration: Database migration required (see /docs/migrations/v1.1.0.md)
```

---

### 11. `security.md`

**Purpose:**

- Document all security requirements, controls, and practices applied in the project, audit results, security frameworks recommendations, incident response plans, compliance status, and records of found vulnerabilities.

**Required content:**

- Security frameworks and standards adopted (e.g., OWASP Top 10, ASVS)
- Password, authentication, encryption policies
- Audit results, pentests, automated scans
- Identified and resolved vulnerabilities
- Incident response plan
- Compliance status (PCI DSS, GDPR, etc)
- Security training and awareness programs

**Validation Requirements:**
- Security reviews must be scheduled and documented
- Vulnerability remediation must include timelines
- Compliance status must be verified annually

**Example:**

```
Last Updated: 2024-01-18 | Updated by: Security Team

Security Framework Adoption:
- OWASP ASVS Level 2 for backend APIs
- OWASP Top 10 2021 compliance verified
- OWASP LLM Top 10 for AI agent security
- CIS Controls implementation (85% complete)

Security Policies:
- Passwords: Minimum 12 characters, bcrypt hashing (12 rounds)
- Session management: JWT with 24h expiration + refresh tokens
- Data encryption: TLS 1.3 in transit, AES-256 at rest
- Access control: RBAC with principle of least privilege

Recent Security Activities:
- External penetration test: 2024-01-10 (2 medium findings, resolved)
- SAST scan: 2024-01-15 (clean results)
- Dependency audit: 2024-01-16 (3 low-risk updates applied)

Incident Response:
- Security incident hotline: security@company.com
- Response time: <4 hours for high severity
- Escalation path: Security Team → CISO → Executive Team

Compliance Status:
- GDPR: Compliant (last audit: 2023-12-15)
- SOC 2 Type II: In progress (audit scheduled 2024-02-01)
- ISO 27001: Planning phase
```

---

### 12. `tests.md`

**Purpose:**

- Document the testing strategy (unit, integration, end-to-end, smoke, stress, fuzzing), coverage, tools, CI/CD automation, main scenarios, and quality metrics.

**Required content:**

- Testing strategy and types adopted
- Test coverage (percentage per module)
- Tools used (Jest, Cypress, Postman, etc)
- CI/CD pipeline status
- Main bugs found through tests
- Manual vs. automated tests
- Performance testing results
- Test data management strategy

**Validation Requirements:**
- Coverage thresholds must be defined and monitored
- Critical user journeys must have automated tests
- Test execution time must be tracked and optimized

**Example:**

```
Last Updated: 2024-01-16 | Updated by: QA Team

Testing Strategy:
- Unit tests: Jest (target: >85% coverage)
- Integration tests: Supertest for API testing
- E2E tests: Cypress for critical user journeys
- Performance tests: Artillery for load testing
- Security tests: OWASP ZAP automated scans

Current Metrics:
- Unit test coverage: 87% (target: 85%)
- Integration test coverage: 92%
- E2E test scenarios: 16 critical paths covered
- Test execution time: 8 minutes (CI pipeline)
- Test reliability: 98.5% (green builds)

Performance Testing Results:
- Load test: 500 concurrent users, 99th percentile response time <1s
- Stress test: System stable up to 1000 concurrent users
- Database performance: 10,000 queries/second sustained

Test Automation:
- CI/CD: Tests run on every PR and main branch commit
- Nightly: Full regression suite + security scans
- Weekly: Performance and load testing
- Release: Complete test suite + manual verification

Quality Gates:
- All tests must pass before merge
- Coverage cannot decrease
- Performance benchmarks must be met
- Security scans must show no new high/critical issues
```

---

### 13. `index-memory-bank.md`

**Purpose:**

- Serve as the central index of the memory bank, listing all required files, description of each one's function, usage examples, update instructions, and minimum recommended maintenance frequency.
- Must be updated whenever a new relevant file is added or removed from the memory bank.

**Required content:**

- List of all required and optional memory bank files
- Brief description of the function of each file
- Summary instructions for update/maintenance
- Minimum recommended update frequency
- Cross-reference validation rules
- Quality control checklist

**Validation Requirements:**
- Index must be updated within 24 hours of any memory bank changes
- All referenced files must exist and be current
- Quality metrics must be tracked and reported

**Example:**

```
# Memory Bank Index

Last Updated: 2024-01-18 | Updated by: System Administrator

## Core Documentation Files

### Technical Foundation
- **languages.md**: Project technologies, frameworks, and tools
  - Update trigger: New technology adoption or version changes
  - Validation: All entries must include versions and rationale
  - Review frequency: Monthly

- **integrations.md**: External integrations, providers, APIs
  - Update trigger: New integrations or security reviews
  - Validation: Security assessment required for all active integrations
  - Review frequency: Quarterly

- **architecture.md**: System architecture, diagrams, flows
  - Update trigger: Architectural changes or new system components
  - Validation: Diagrams must match implementation
  - Review frequency: After major releases

### Development Lifecycle
- **features.md**: Developed features, status, owners
  - Update trigger: Feature completion or status changes
  - Validation: All features must have assigned owners
  - Review frequency: Weekly during active development

- **fixes.md**: Bugs, vulnerabilities, applied improvements
  - Update trigger: Bug reports, security fixes, or improvements
  - Validation: All fixes must reference commits and include validation
  - Review frequency: After each fix

- **version.md**: Version and release control
  - Update trigger: Each release or deployment
  - Validation: Must follow semantic versioning
  - Review frequency: With each release

### System Components
- **frontend.md**: Frontend structure and evolution
  - Update trigger: Frontend architectural changes
  - Validation: Performance metrics must be current
  - Review frequency: Monthly

- **backend.md**: Backend structure and evolution
  - Update trigger: Backend changes or new endpoints
  - Validation: API documentation must be complete
  - Review frequency: Monthly

- **communication.md**: Inter-system communication patterns
  - Update trigger: API changes or new communication protocols
  - Validation: All endpoints must have examples
  - Review frequency: Quarterly

### Operations & Quality
- **project-status.md**: Current project health and status
  - Update trigger: Weekly status updates or significant changes
  - Validation: Health indicators must be justified
  - Review frequency: Weekly

- **security.md**: Security controls, audits, incidents
  - Update trigger: Security reviews, incidents, or policy changes
  - Validation: All vulnerabilities must have remediation plans
  - Review frequency: After security activities

- **tests.md**: Testing strategy, coverage, and tools
  - Update trigger: Testing strategy changes or coverage updates
  - Validation: Coverage metrics must be current
  - Review frequency: Monthly

## Quality Control Checklist

### Daily Checks
- [ ] All files have current timestamps
- [ ] No broken cross-references between files
- [ ] Critical issues are properly escalated

### Weekly Checks
- [ ] project-status.md updated
- [ ] features.md reflects current development state
- [ ] No files older than their review frequency

### Monthly Checks
- [ ] All technical documentation reviewed
- [ ] Architecture diagrams current with implementation
- [ ] Performance metrics updated

### Quarterly Checks
- [ ] Security documentation reviewed
- [ ] Integration security assessments current
- [ ] Compliance status verified

## Maintenance Instructions

1. **File Updates**: Always include update timestamp and responsible person
2. **Cross-References**: Verify links between related documents
3. **Version Control**: Commit memory bank changes with descriptive messages
4. **Validation**: Run quality checks before committing changes
5. **Approval**: Security and architecture changes require team review

## Emergency Procedures

- **Critical Issues**: Update relevant files immediately, notify team
- **Security Incidents**: Follow security.md incident response procedures
- **System Outages**: Document in project-status.md with timeline
- **Data Loss**: Restore from version control, validate completeness

## Metrics and Health

- **File Freshness**: 95% of files updated within review frequency
- **Cross-Reference Integrity**: 100% of links must be valid
- **Validation Compliance**: All files must pass quality checks
- **Team Engagement**: All team members must contribute to memory bank

---

**Last Quality Check**: 2024-01-18 | Status: ✅ All systems green
**Next Scheduled Review**: 2024-01-25
**Outstanding Actions**: None
```

---

## Quality Control and Validation

### File-Level Validation Requirements

All memory bank files must include:
1. **Header with last update date and responsible person**
2. **Required content fields as specified for each file type**
3. **Cross-references to related files when applicable**
4. **Version control integration (proper commit messages)**

### System-Level Validation

1. **Consistency Checks**
   - Cross-reference integrity between files
   - Version alignment across all documentation
   - No conflicting information between files

2. **Completeness Checks**
   - All required files present and current
   - No missing critical information
   - All active systems/features documented

3. **Quality Metrics**
   - File freshness (updated within review frequency)
   - Content accuracy (matches implementation)
   - Team engagement (all team members contributing)

### Automated Validation Tools

Teams should implement automated checks for:
- File existence and structure validation
- Cross-reference link verification
- Date freshness monitoring
- Required field presence validation
- Commit message compliance

---

## Emergency Procedures

### When to Bypass Normal Documentation Workflow

Emergency situations that may require immediate action before documentation:
1. **Critical Security Incidents**: Active exploits or data breaches
2. **Production System Failures**: Complete system outages
3. **Data Loss Events**: Risk of permanent data loss

### Emergency Documentation Protocol

1. **Immediate Response** (within 1 hour)
   - Take necessary emergency action
   - Create emergency log entry in relevant memory bank file
   - Notify team through designated emergency channels

2. **Follow-up Documentation** (within 24 hours)
   - Complete full documentation in appropriate memory bank files
   - Update project-status.md with incident details
   - Conduct post-incident review and update procedures

3. **Review and Improvement** (within 72 hours)
   - Team review of emergency response
   - Update emergency procedures if needed
   - Implement preventive measures

---

## Notes and Recommendations for the Agent

- The agent is responsible for ensuring continuous updating, traceability, and documentation accuracy of the entire memory bank.
- Documentation must be objective, precise, always with date and responsible person identified.
- Register links to tasks, issues, pull requests, diagrams, images, and any relevant artifacts for each item.
- The memory bank is fundamental for governance, continuity, team transfers, compliance, and future audits.
- Do not fail to update documents after fixes, audits, deliveries, and critical decisions.
- Promote a collaborative documentation culture, encouraging the whole team to participate in the memory bank.
- Implement validation checks to ensure documentation quality and consistency.
- Use automation tools where possible to maintain documentation freshness and accuracy.

---

**END OF FILE**