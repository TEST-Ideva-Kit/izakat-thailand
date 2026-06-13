# AGENT.md

This document guides AI coding assistants working on the iZakat Thailand repository.

## Project Overview
The iZakat Thailand project aims to provide an accurate and user-friendly application for calculating and managing Zakat obligations according to Shafi'i jurisprudence. It serves Muslims seeking to fulfill their religious financial duties with transparency and ease, ensuring compliance with Islamic financial rulings.

## Tech Stack
*   **Languages**: TypeScript, Node.js, React
*   **Frameworks**: Next.js, Express.js
*   **Databases**: PostgreSQL
*   **Caches**: Redis
*   **Runtime Versions**: Node.js (latest LTS), React/Next.js (latest stable), PostgreSQL (latest stable), Redis (latest stable)

## Repository Structure
*   `apps/backend/`: Contains the Node.js/Express.js backend API service.
*   `apps/frontend/`: Houses the Next.js React frontend application.
*   `specs/`: Stores project documentation, including the Constitution, feature specifications, and implementation plans.

## Architecture Decisions
*   **Jurisprudence-First Calculation**: All calculation logic must strictly adhere to Shafi'i jurisprudence principles (asset categorization, Nisab, Hawl, rates).
*   **API-First & Modularity**: The backend is designed as a distinct API service, promoting modularity and facilitating integration.
*   **User-Centric Design & Accessibility**: The application must be intuitive and WCAG 2.1 AA compliant.
*   **Data Integrity & Security**: Robust security measures (OAuth2, RBAC, MFA, encryption, audit logs) are paramount for sensitive financial data.
*   **Auditability & Transparency**: Detailed calculation breakdowns and auditable receipts are mandatory for all Zakat fulfillment.

## Coding Conventions
*   All code changes must undergo mandatory peer review.
*   Adherence to the principles outlined in the iZakat Thailand Constitution is non-negotiable.
*   Prioritize correctness, security, and performance in all implementations.
*   Follow Agile methodology with iterative development cycles.
*   Embrace type safety with TypeScript.

## Testing Requirements
*   Unit, integration, and end-to-end tests are required for all new features and significant changes.
*   The core Zakat calculation engine must have extensive test coverage.
*   Tests should verify adherence to Shafi'i jurisprudence rules, security requirements, and functional acceptance scenarios defined in `specs/`.
*   Utilize Jest, React Testing Library, Supertest, and Cypress as per the development plan.

## Key Rules
*   [x] All Zakat calculations must strictly adhere to Shafi'i jurisprudence.
*   [x] The application must be accessible, meeting WCAG 2.1 AA standards.
*   [x] User financial data must be highly secured (encryption, secure auth, RBAC, audit logs).
*   [x] All Zakat calculations, payments, and data exports must be auditable.
*   [x] Design must be modular and API-first.
*   [x] Adhere to strict data privacy principles.
*   [x] All code changes must undergo mandatory peer review.
*   [x] The project's Constitution supersedes all other project practices and documentation.