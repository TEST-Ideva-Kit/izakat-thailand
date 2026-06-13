
# iZakat Thailand Constitution


## Core Principles

### Jurisprudence-First Calculation

All calculations must strictly adhere to Shafi'i jurisprudence. This includes asset categorization, nisab thresholds, hawl calculations, and zakat rates (2.5% for applicable wealth). Prioritize accuracy and compliance with Islamic financial rulings.


### User-Centric Design &amp; Accessibility

The application must be intuitive, accessible (WCAG AA compliant), and provide clear, understandable guidance. User experience should be seamless, with a focus on transparency in calculations and reporting. Support for localization and multi-language is essential.


### Data Integrity &amp; Security (NON-NEGOTIABLE)

User financial data is highly sensitive. Implement robust encryption, secure authentication (MFA, OAuth2), role-based access control, and comprehensive audit logs. Ensure compliance with data privacy regulations and build user trust through transparent data handling policies.


### Auditability &amp; Transparency

All zakat calculations, payments, and data exports must be auditable. Provide detailed breakdowns, receipts, and export options (PDF/CSV). Maintain clear records of changes and fulfillment actions.


### Modularity &amp; API-First

Design the application with a modular architecture and API-first approach. This facilitates easier integration, maintenance, and future expansion of features and services.


## Technical &amp; Security Requirements


**Technology Stack**: Frontend: React + Next.js. Backend: Node.js/Express or Python FastAPI. Database: PostgreSQL, Redis.
**Security**: Implement OAuth2/OpenID Connect, RBAC, MFA. Encrypt sensitive data at rest and in transit. Regular security audits and vulnerability scanning.
**Observability**: Comprehensive logging, metrics, and error tracking are mandatory for all services.
**Privacy**: Adhere to strict data privacy principles, including consent management and audit trails for data access.


## Development &amp; Review Process


**Development Workflow**: Agile methodology with iterative development cycles. Prioritize features based on user stories and business impact.
**Code Reviews**: All code changes must undergo mandatory peer review, focusing on correctness, adherence to principles, security, and performance.
**Testing**: Unit, integration, and end-to-end tests are required for all new features and significant changes. Calculation engine must have extensive test coverage.
**Deployment**: Utilize CI/CD pipelines for automated testing and deployment. Dockerization for all services.


## Governance


This Constitution supersedes all other project practices and documentation.
Amendments require a formal proposal, review by stakeholders (including subject matter experts on Shafi'i jurisprudence), and documented migration plans.
All Pull Requests and code reviews must verify compliance with this Constitution.
Complexity must always be justified with clear benefits.
Use `specs/SPECIFICATION.md` for runtime development guidance.


**Version**: 1.0.0 | **Ratified**: 2026-06-13 | **Last Amended**: 2026-06-13