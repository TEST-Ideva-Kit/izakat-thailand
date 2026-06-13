<!-- Sync Impact Report:
- Version Change: 1.0.0 (New Constitution)
- Added Principles: Jurisprudence-First Calculation, User-Centric Design & Accessibility, Data Integrity & Security, Auditability & Transparency, Modularity & API-First
- Modified Principles: None
- Removed Principles: None
-->
# iZakat Thailand Constitution
<!-- Example: Spec Constitution, TaskFlow Constitution, etc. -->

## Core Principles

### Jurisprudence-First Calculation
<!-- Example: I. Library-First -->
All calculations must strictly adhere to Shafi'i jurisprudence. This includes asset categorization, nisab thresholds, hawl calculations, and zakat rates (2.5% for applicable wealth). Prioritize accuracy and compliance with Islamic financial rulings.
<!-- Example: Every feature starts as a standalone library; Libraries must be self-contained, independently testable, documented; Clear purpose required - no organizational-only libraries -->

### User-Centric Design & Accessibility
<!-- Example: II. CLI Interface -->
The application must be intuitive, accessible (WCAG AA compliant), and provide clear, understandable guidance. User experience should be seamless, with a focus on transparency in calculations and reporting. Support for localization and multi-language is essential.
<!-- Example: Every library exposes functionality via CLI; Text in/out protocol: stdin/args → stdout, errors → stderr; Support JSON + human-readable formats -->

### Data Integrity & Security (NON-NEGOTIABLE)
<!-- Example: III. Test-First (NON-NEGOTIABLE) -->
User financial data is highly sensitive. Implement robust encryption, secure authentication (MFA, OAuth2), role-based access control, and comprehensive audit logs. Ensure compliance with data privacy regulations and build user trust through transparent data handling policies.
<!-- Example: TDD mandatory: Tests written → User approved → Tests fail → Then implement; Red-Green-Refactor cycle strictly enforced -->

### Auditability & Transparency
<!-- Example: IV. Integration Testing -->
All zakat calculations, payments, and data exports must be auditable. Provide detailed breakdowns, receipts, and export options (PDF/CSV). Maintain clear records of changes and fulfillment actions.
<!-- Example: Focus areas requiring integration tests: New library contract tests, Contract changes, Inter-service communication, Shared schemas -->

### Modularity & API-First
<!-- Example: V. Observability, VI. Versioning & Breaking Changes, VII. Simplicity -->
Design the application with a modular architecture and API-first approach. This facilitates easier integration, maintenance, and future expansion of features and services.
<!-- Example: Text I/O ensures debuggability; Structured logging required; Or: MAJOR.MINOR.BUILD format; Or: Start simple, YAGNI principles -->

## Technical & Security Requirements
<!-- Example: Additional Constraints, Security Requirements, Performance Standards, etc. -->

**Technology Stack**: Frontend: React + Next.js. Backend: Node.js/Express or Python FastAPI. Database: PostgreSQL, Redis.
**Security**: Implement OAuth2/OpenID Connect, RBAC, MFA. Encrypt sensitive data at rest and in transit. Regular security audits and vulnerability scanning.
**Observability**: Comprehensive logging, metrics, and error tracking are mandatory for all services.
**Privacy**: Adhere to strict data privacy principles, including consent management and audit trails for data access.
<!-- Example: Technology stack requirements, compliance standards, deployment policies, etc. -->

## Development & Review Process
<!-- Example: Development Workflow, Review Process, Quality Gates, etc. -->

**Development Workflow**: Agile methodology with iterative development cycles. Prioritize features based on user stories and business impact.
**Code Reviews**: All code changes must undergo mandatory peer review, focusing on correctness, adherence to principles, security, and performance.
**Testing**: Unit, integration, and end-to-end tests are required for all new features and significant changes. Calculation engine must have extensive test coverage.
**Deployment**: Utilize CI/CD pipelines for automated testing and deployment. Dockerization for all services.
<!-- Example: Code review requirements, testing gates, deployment approval process, etc. -->

## Governance
<!-- Example: Constitution supersedes all other practices; Amendments require documentation, approval, migration plan -->

This Constitution supersedes all other project practices and documentation.
Amendments require a formal proposal, review by stakeholders (including subject matter experts on Shafi'i jurisprudence), and documented migration plans.
All Pull Requests and code reviews must verify compliance with this Constitution.
Complexity must always be justified with clear benefits.
Use `specs/SPECIFICATION.md` for runtime development guidance.
<!-- Example: All PRs/reviews must verify compliance; Complexity must be justified; Use [GUIDANCE_FILE] for runtime development guidance -->

**Version**: 1.0.0 | **Ratified**: 2026-06-13 | **Last Amended**: 2026-06-13