# Implementation Plan: Zakat Calculation and Management

**Branch**: `001-description-yet-project` | **Date**: 2026-06-13 | **Spec**: specs/001-description-yet-project/spec.md
**Input**: Feature specification from `/specs/001-description-yet-project/spec.md`

## Summary

This feature aims to develop a Zakat calculation and management application adhering strictly to Shafi'i jurisprudence. The application will provide accurate Zakat calculations based on user-inputted assets and liabilities, track financial data securely, and generate auditable receipts. The technical stack will comprise a React/Next.js frontend for user interaction and a Node.js/Express backend for core logic and data management, leveraging PostgreSQL for data storage and Redis for caching. Key focus areas include ensuring jurisprudential accuracy, robust security, WCAG AA accessibility, and a transparent, auditable user experience.

## Technical Context

**Language/Version**: Frontend: TypeScript/React/Next.js (latest stable). Backend: TypeScript/Node.js (latest LTS), Express.js. Database: PostgreSQL (latest stable). Cache: Redis (latest stable).
**Primary Dependencies**: React, Next.js, Express.js, TypeORM (or similar ORM for PostgreSQL), `ioredis`, `@sentry/nextjs` (for observability), `class-validator` (for input validation), JWT for authentication.
**Storage**: PostgreSQL (user profiles, assets, liabilities, calculation history, payment records). Redis (session management, caching).
**Testing**: Jest, React Testing Library (Frontend). Jest, Supertest (Backend API). End-to-end testing with Cypress.
**Target Platform**: Web application accessible via modern browsers.
**Project Type**: Full-stack Web Application with a distinct backend API service.
**Performance Goals**: Frontend: Lighthouse score of 90+, fast page loads. Backend: p95 response time < 200ms for core Zakat calculation API.
**Constraints**: WCAG 2.1 AA compliance, GDPR/data privacy compliance, OWASP Top 10 security adherence, calculations must be 100% accurate per Shafi'i jurisprudence.
**Scale/Scope**: Designed for individual users; scalable to accommodate a growing user base through standard cloud deployment practices.

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

*   **Jurisprudence-First Calculation**: The core of this feature. All calculation logic, Nisab determination (based on current gold/silver prices), Hawl tracking, and asset/liability categorization will be meticulously implemented to align with Shafi'i jurisprudence. This will be a primary focus during development and testing.
*   **User-Centric Design & Accessibility**: WCAG 2.1 AA compliance is a stated requirement (FR-012, SC-005). The UI will be designed for intuitiveness, with clear input forms for assets/liabilities and transparent presentation of calculations and receipts.
*   **Data Integrity & Security**: User financial data is highly sensitive (Constitution, Technical Req). Implement robust security measures including OAuth2/OpenID Connect for authentication, Role-Based Access Control (RBAC) for any future roles, Multi-Factor Authentication (MFA), encryption of sensitive data at rest (PostgreSQL TDE or column-level encryption) and in transit (TLS/SSL). Comprehensive audit logs for all data access and modifications will be maintained.
*   **Auditability & Transparency**: Detailed breakdowns of Zakat calculations will be provided (FR-008). Users can record payments and generate auditable receipts (FR-009, FR-010). Audit logs will further enhance transparency.
*   **Modularity & API-First**: The backend will be developed as a distinct API service (e.g., using Express.js) that the Next.js frontend will consume. This promotes modularity and allows for potential future API consumers.
*   **Technology Stack**: Adheres to specified stack: React/Next.js (Frontend), Node.js/Express (Backend), PostgreSQL (Database), Redis (Caching).
*   **Security**: OAuth2/OpenID Connect, RBAC, MFA, encryption, regular security audits (part of development process).
*   **Observability**: Comprehensive logging (e.g., Winston), metrics (e.g., Prometheus client), and error tracking (e.g., Sentry integration via `@sentry/nextjs` on frontend and Sentry SDK on backend) will be implemented.
*   **Privacy**: Adherence to data privacy principles will be managed through consent mechanisms (where applicable) and robust audit trails for data access.
*   **Development Workflow**: Agile methodology, iterative development, mandatory peer reviews for all code, comprehensive unit, integration, and E2E testing, CI/CD pipeline for automated builds and deployments, Dockerization of services.

## Project Structure

The chosen structure is **Option 2: Web application**, adapted for a monorepo context where `apps/backend` hosts the Node.js/Express API and `apps/frontend` hosts the Next.js React application. This separation aligns with the API-first principle and modular design.

```text
# Monorepo root
.
├── apps/
│   ├── backend/          # Node.js/Express Backend service
│   │   ├── src/
│   │   │   ├── api/          # API routes and controllers
│   │   │   ├── config/       # Application configuration
│   │   │   ├── models/       # Database models (entities)
│   │   │   ├── services/     # Business logic services
│   │   │   ├── middleware/   # Express middleware
│   │   │   └── index.ts      # Application entry point
│   │   ├── tests/            # Backend tests (unit, integration)
│   │   │   ├── unit/
│   │   │   └── integration/
│   │   └── package.json
│   │
│   └── frontend/         # Next.js Frontend application
│       ├── src/
│       │   ├── components/   # Reusable UI components
│       │   ├── pages/        # Next.js pages
│       │   ├── services/     # API client services
│       │   ├── styles/       # Global styles
│       │   └── types/        # TypeScript types
│       ├── tests/            # Frontend tests (unit, integration)
│       ├── next.config.js
│       └── package.json
│
├── specs/
│   └── 001-description-yet-project/
│       ├── plan.md
│       ├── spec.md
│       └── checklists/
│           └── requirements.md
├── .gitignore
├── README.md
└── ... (other monorepo configurations)
```

**Structure Decision**: The selected structure is **Option 2: Web application**, adapted for a monorepo context.

## Complexity Tracking

No significant violations of the Constitution are anticipated that require justification at this stage. The complexity of implementing accurate Shafi'i jurisprudence calculations and robust security measures is inherent to the requirements and will be managed through thorough planning and testing.

## Phased Delivery Plan and Risks

**Phase 0: Research & Design (1-2 Sprints)**
*   **Tasks**:
    *   Deep dive into Shafi'i jurisprudence for Zakat calculation specifics (asset types, Nisab values for gold/silver, Hawl period, eligible deductions). Consult external resources or SMEs if needed.
    *   Define detailed data models for `User Profile`, `Asset`, `Liability`, `Zakat Calculation`, and `Payment Record`.
    *   Design backend API endpoints for user management, asset/liability CRUD, Zakat calculation, and payment recording.
    *   Design frontend component structure and user flows for data input, calculation display, and receipt generation.
    *   Finalize security architecture (authentication, authorization, data encryption strategy).
    *   Define observability strategy (logging, metrics, error tracking implementation details).
*   **Deliverables**: Detailed Data Model (`data-model.md`), API Contract (`contracts/`), Frontend Component/Flow Diagrams, Security Design Document.
*   **Risks**:
    *   **High**: Misinterpretation or incomplete understanding of Shafi'i jurisprudence rules, leading to inaccurate calculations. (Mitigation: Consult experts, extensive cross-verification with test cases).
    *   **Medium**: Underestimation of complexity in multi-currency handling or dynamic Nisab calculation. (Mitigation: Prioritize clear requirements and robust testing).
    *   **Low**: Scope creep in initial design phase. (Mitigation: Strict adherence to user stories and requirements).

**Phase 1: Backend Core Implementation (2-3 Sprints)**
*   **Tasks**:
    *   Set up PostgreSQL database schema based on the data model.
    *   Implement user authentication and authorization (OAuth2, JWT, RBAC).
    *   Develop CRUD APIs for User Profile, Assets, and Liabilities.
    *   Implement the core Zakat calculation engine, including Nisab determination (integrating with a reliable source for gold/silver prices or a configured default), Hawl tracking, and application of the 2.5% rate.
    *   Develop API endpoint for triggering Zakat calculation.
    *   Implement secure storage for sensitive data and audit logging.
*   **Deliverables**: Functional backend API for core data management and Zakat calculation. Unit and integration tests for backend services and calculation engine.
*   **Risks**:
    *   **High**: Bugs in the calculation engine leading to incorrect Zakat amounts. (Mitigation: Comprehensive unit tests with predefined Shafi'i jurisprudence test cases, thorough integration testing).
    *   **Medium**: Security vulnerabilities in authentication/authorization or data handling. (Mitigation: Peer code reviews focused on security, static analysis tools, integration with security libraries).
    *   **Low**: Performance bottlenecks in the calculation engine for complex user data. (Mitigation: Profiling and optimization, caching strategies).

**Phase 2: Frontend Implementation & Integration (2-3 Sprints)**
*   **Tasks**:
    *   Develop frontend components for user registration/login.
    *   Implement UI for adding, editing, and viewing assets and liabilities, including multi-currency support.
    *   Develop UI to display the calculated Zakat amount with a detailed breakdown.
    *   Implement functionality to record Zakat payments and generate PDF receipts.
    *   Integrate frontend with backend APIs.
    *   Implement WCAG AA accessibility standards across all user-facing components.
    *   Integrate Sentry for frontend error tracking.
*   **Deliverables**: Functional user interface for Zakat management, integrated with backend services. Basic accessibility compliance.
*   **Risks**:
    *   **High**: Poor user experience or difficulty in data entry/comprehension. (Mitigation: User testing, iterative UI refinement, clear labeling and guidance).
    *   **Medium**: Issues with PDF receipt generation or formatting. (Mitigation: Use a reliable PDF generation library, rigorous testing with varied data).
    *   **Low**: Cross-browser compatibility issues. (Mitigation: Adherence to web standards, testing on major browsers).

**Phase 3: Testing, Refinement & Deployment Prep (1-2 Sprints)**
*   **Tasks**:
    *   Conduct comprehensive end-to-end testing covering all user stories and edge cases.
    *   Perform security audits and penetration testing.
    *   Conduct accessibility audits and address any identified issues.
    *   Implement and optimize logging, metrics, and error tracking.
    *   Refine UI/UX based on feedback.
    *   Prepare Docker images for backend and frontend services.
    *   Configure CI/CD pipeline for automated builds, tests, and deployments.
*   **Deliverables**: Fully tested, secure, and accessible application. Ready-to-deploy Docker images. Automated CI/CD pipeline.
*   **Risks**:
    *   **High**: Critical security vulnerabilities discovered late in the cycle. (Mitigation: Proactive security reviews throughout development, engage security experts if possible).
    *   **Medium**: Performance issues under load. (Mitigation: Load testing, database query optimization, caching tuning).
    *   **Low**: Deployment configuration errors. (Mitigation: Staging environment testing, thorough documentation).

**Phase 4: Post-Deployment Monitoring & Iteration (Ongoing)**
*   **Tasks**:
    *   Monitor application performance, errors, and security logs.
    *   Gather user feedback for future iterations.
    *   Address any post-deployment bugs or issues.
*   **Deliverables**: Stable, monitored application. Iterative improvements based on feedback.
*   **Risks**:
    *   **High**: Failure to adequately monitor and respond to critical issues. (Mitigation: Robust alerting and on-call procedures).
    *   **Medium**: Stale jurisprudence data (e.g., Nisab values). (Mitigation: Plan for regular updates to financial data if required by jurisprudence).