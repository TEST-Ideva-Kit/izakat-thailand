# Tasks: Zakat Calculation and Management

**Input**: Design documents from `/specs/001-description-yet-project/`
**Prerequisites**: plan.md, spec.md

**Tests**: Not included (not explicitly requested in spec).

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (US1, US2, US3)
- Paths follow monorepo structure: `apps/backend/src/` and `apps/frontend/src/`

---

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Initialize monorepo structure, tooling, and containerization.

- [ ] T001 Initialize monorepo root structure with `apps/backend/` and `apps/frontend/` directories per implementation plan
- [ ] T002 Set up Node.js/Express/TypeScript project in `apps/backend/` with `package.json`, `tsconfig.json`, and `src/index.ts` entry point
- [ ] T003 [P] Set up Next.js/TypeScript project in `apps/frontend/` with `package.json`, `tsconfig.json`, and `next.config.js`
- [ ] T004 [P] Configure ESLint, Prettier, and shared TypeScript config at monorepo root (`eslint.config.js`, `.prettierrc`, `tsconfig.base.json`)
- [ ] T005 [P] Configure Docker and Docker Compose for local development in `docker-compose.yml` (backend, frontend, postgres, redis services)

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure that MUST be complete before ANY user story can be implemented.

**⚠️ CRITICAL**: No user story work can begin until this phase is complete.

- [ ] T006 Configure PostgreSQL connection and TypeORM migrations framework in `apps/backend/src/config/database.ts`
- [ ] T007 [P] Configure Redis session management with `ioredis` in `apps/backend/src/config/redis.ts`
- [ ] T008 [P] Set up environment variable management with validation in `apps/backend/src/config/env.ts` and `apps/frontend/src/config/env.ts`
- [ ] T009 [P] Configure Winston structured logging in `apps/backend/src/config/logger.ts`
- [ ] T010 [P] Set up Sentry error tracking in `apps/backend/src/config/sentry.ts` and `apps/frontend/src/lib/sentry.ts`
- [ ] T011 Create User Profile entity and migration in `apps/backend/src/models/user-profile.entity.ts` (id, email, name, jurisprudence settings, createdAt)
- [ ] T012 Implement JWT authentication middleware and OAuth2 user registration/login in `apps/backend/src/middleware/auth.ts` and `apps/backend/src/api/auth.controller.ts`
- [ ] T013 [P] Set up Express API router structure and global error handler in `apps/backend/src/api/index.ts` and `apps/backend/src/middleware/error-handler.ts`

**Checkpoint**: Foundation ready — user story implementation can now begin.

---

## Phase 3: User Story 1 — Accurately Calculate Zakat Amount (Priority: P1) 🎯 MVP

**Goal**: Users can input assets and liabilities and receive an accurate, auditable Zakat calculation per Shafi'i jurisprudence, including Nisab and Hawl.

**Independent Test**: A user inputs a defined set of assets and liabilities; the system returns the correct Zakat amount with a full breakdown that matches manual Shafi'i calculations.

### Implementation for User Story 1

- [ ] T014 [P] [US1] Create Asset entity and migration in `apps/backend/src/models/asset.entity.ts` (id, userId, type, value, currency, acquisitionDate, shafiClassification, isZakatable)
- [ ] T015 [P] [US1] Create Liability entity and migration in `apps/backend/src/models/liability.entity.ts` (id, userId, type, amount, currency, dueDate)
- [ ] T016 [P] [US1] Create ZakatCalculation entity and migration in `apps/backend/src/models/zakat-calculation.entity.ts` (id, userId, calculatedAmount, nisabValue, hawlDate, breakdownJson, status, createdAt)
- [ ] T017 [US1] Implement NisabService for gold/silver price lookups and Nisab threshold calculation in `apps/backend/src/services/nisab.service.ts`
- [ ] T018 [US1] Implement HawlService for lunar year (Hawl) tracking per asset class in `apps/backend/src/services/hawl.service.ts`
- [ ] T019 [US1] Implement ZakatCalculationEngine applying 2.5% rate, Nisab check, Hawl tracking, and liability deductions per Shafi'i rules in `apps/backend/src/services/zakat-calculation.service.ts`
- [ ] T020 [US1] Create Zakat calculation API endpoint `POST /api/calculations` with full breakdown response in `apps/backend/src/api/calculations.controller.ts`
- [ ] T021 [US1] Create minimal Asset and Liability input API (`POST/GET /api/assets`, `POST/GET /api/liabilities`) sufficient for US1 in `apps/backend/src/api/assets.controller.ts` and `apps/backend/src/api/liabilities.controller.ts`
- [ ] T022 [P] [US1] Build ZakatInputForm component for asset/liability entry in `apps/frontend/src/components/zakat/ZakatInputForm.tsx`
- [ ] T023 [US1] Build CalculationBreakdown display component showing assets, liabilities, Nisab, Hawl, and final Zakat amount in `apps/frontend/src/components/zakat/CalculationBreakdown.tsx`
- [ ] T024 [US1] Create Zakat calculation page integrating input form and breakdown display in `apps/frontend/src/pages/calculate.tsx`

**Checkpoint**: User Story 1 fully functional — a user can calculate their Zakat independently of all other stories.

---

## Phase 4: User Story 2 — Track Assets and Liabilities (Priority: P2)

**Goal**: Users can add, edit, categorize, and view comprehensive assets and liabilities across multiple currencies.

**Independent Test**: A user can add 10 assets and 5 liabilities in multiple currencies, edit and delete them, and see an aggregated financial overview — all without triggering a Zakat calculation.

### Implementation for User Story 2

- [ ] T025 [P] [US2] Implement full AssetService with create/read/update/delete and Shafi'i categorization in `apps/backend/src/services/asset.service.ts`
- [ ] T026 [P] [US2] Implement full LiabilityService with create/read/update/delete in `apps/backend/src/services/liability.service.ts`
- [ ] T027 [US2] Implement CurrencyConversionService for multi-currency aggregation in `apps/backend/src/services/currency.service.ts`
- [ ] T028 [US2] Extend Asset API with full CRUD routes (`PUT /api/assets/:id`, `DELETE /api/assets/:id`) and filtering in `apps/backend/src/api/assets.controller.ts`
- [ ] T029 [US2] Extend Liability API with full CRUD routes (`PUT /api/liabilities/:id`, `DELETE /api/liabilities/:id`) in `apps/backend/src/api/liabilities.controller.ts`
- [ ] T030 [P] [US2] Build AssetForm component supporting type selection, quantity, currency, and acquisition date in `apps/frontend/src/components/assets/AssetForm.tsx`
- [ ] T031 [P] [US2] Build LiabilityForm component supporting amount, currency, and due date in `apps/frontend/src/components/assets/LiabilityForm.tsx`
- [ ] T032 [US2] Build FinancialOverview component displaying aggregated and individual asset/liability values with currency toggle in `apps/frontend/src/components/assets/FinancialOverview.tsx`
- [ ] T033 [US2] Create Assets and Liabilities management pages with list, add, edit, and delete flows in `apps/frontend/src/pages/assets.tsx` and `apps/frontend/src/pages/liabilities.tsx`

**Checkpoint**: User Stories 1 and 2 both independently functional.

---

## Phase 5: User Story 3 — Record Zakat Payment and Generate Receipt (Priority: P3)

**Goal**: Users can mark a calculated Zakat amount as paid and download an auditable PDF receipt with payment details.

**Independent Test**: A user records a Zakat payment for a prior calculation and downloads a PDF receipt containing the Zakat amount, payment date, and user details.

### Implementation for User Story 3

- [ ] T034 [P] [US3] Create PaymentRecord entity and migration in `apps/backend/src/models/payment-record.entity.ts` (id, userId, calculationId, paidAmount, paymentDate, notes, receiptPath, createdAt)
- [ ] T035 [US3] Implement PaymentService for recording and retrieving Zakat payments in `apps/backend/src/services/payment.service.ts`
- [ ] T036 [US3] Create payment recording API endpoint `POST /api/payments` and list endpoint `GET /api/payments` in `apps/backend/src/api/payments.controller.ts`
- [ ] T037 [US3] Implement PDF receipt generation service using a PDF library (e.g., `pdfkit`) in `apps/backend/src/services/receipt.service.ts`
- [ ] T038 [US3] Add receipt download endpoint `GET /api/payments/:id/receipt` returning a PDF stream in `apps/backend/src/api/payments.controller.ts`
- [ ] T039 [P] [US3] Build PaymentForm component for recording payment date, amount, and optional notes in `apps/frontend/src/components/payments/PaymentForm.tsx`
- [ ] T040 [US3] Build ReceiptDownload component with download button and confirmation state in `apps/frontend/src/components/payments/ReceiptDownload.tsx`
- [ ] T041 [US3] Create payment management page linking calculation result → payment recording → receipt download in `apps/frontend/src/pages/payments.tsx`

**Checkpoint**: All three user stories independently functional and verified.

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Accessibility, security hardening, observability, and deployment readiness across all stories.

- [ ] T042 [P] Implement WCAG 2.1 AA accessibility attributes (ARIA labels, keyboard navigation, contrast) across all frontend components in `apps/frontend/src/components/`
- [ ] T043 [P] Add column-level encryption for sensitive user financial fields in `apps/backend/src/config/encryption.ts` and apply to Asset/Liability/PaymentRecord entities
- [ ] T044 [P] Implement comprehensive audit logging middleware for all data access and mutations in `apps/backend/src/middleware/audit.ts`
- [ ] T045 [P] Add Shafi'i jurisprudence guidance, scholarly disclaimers, and contextual help content in `apps/frontend/src/components/guidance/`
- [ ] T046 Configure GitHub Actions CI/CD pipeline for lint, test, build, and Docker publish in `.github/workflows/ci.yml`
- [ ] T047 [P] Create production Docker configurations and `docker-compose.prod.yml` with TLS, env secrets, and health checks
- [ ] T048 Conduct OWASP Top 10 security hardening review across backend API (input validation, rate limiting, CSP headers, SQL injection guards)

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies — start immediately
- **Foundational (Phase 2)**: Depends on Phase 1 completion — BLOCKS all user stories
- **User Story 1 (Phase 3)**: Depends on Phase 2 completion
- **User Story 2 (Phase 4)**: Depends on Phase 2; may reuse US1 entities (Asset, Liability)
- **User Story 3 (Phase 5)**: Depends on Phase 2; references ZakatCalculation from US1
- **Polish (Phase 6)**: Depends on all desired user stories being complete

### User Story Dependencies

- **US1 (P1)**: Can start after Phase 2 — no dependency on US2 or US3
- **US2 (P2)**: Can start after Phase 2 — extends Asset/Liability entities from US1
- **US3 (P3)**: Can start after Phase 2 — depends on ZakatCalculation entity from US1

### Within Each User Story

- Entities before services
- Services before API controllers
- Backend controllers before frontend pages
- Core components before composite pages

### Parallel Opportunities

- T002 and T003 (backend + frontend setup) can run in parallel
- T014, T015, T016 (entity creation) can all run in parallel
- T017 and T022 (NisabService + ZakatInputForm) are backend vs frontend — parallel
- T025 and T026 (AssetService + LiabilityService) can run in parallel
- T030 and T031 (AssetForm + LiabilityForm) can run in parallel
- T034 and T039 (PaymentRecord entity + PaymentForm component) can run in parallel

---

## Parallel Example: User Story 1

```bash
# Launch entity creation in parallel (all different files):
Task T014: Create Asset entity in apps/backend/src/models/asset.entity.ts
Task T015: Create Liability entity in apps/backend/src/models/liability.entity.ts
Task T016: Create ZakatCalculation entity in apps/backend/src/models/zakat-calculation.entity.ts

# After entities: run service chain sequentially
Task T017: NisabService → Task T018: HawlService → Task T019: ZakatCalculationEngine

# Frontend can start in parallel with backend services:
Task T022: ZakatInputForm component (no backend dependency to start building)
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational (CRITICAL — blocks all stories)
3. Complete Phase 3: User Story 1 (T014–T024)
4. **STOP and VALIDATE**: Manually verify Zakat calculations against Shafi'i jurisprudence
5. Deploy/demo if validated

### Incremental Delivery

1. Setup + Foundational → Foundation ready
2. User Story 1 → Validate Zakat calculation accuracy → Deploy MVP
3. User Story 2 → Full asset/liability tracking → Deploy
4. User Story 3 → Payment recording + PDF receipts → Deploy
5. Polish → Accessibility audit, security hardening, CI/CD

### Parallel Team Strategy

With multiple developers:

1. Complete Phase 1 + Phase 2 together
2. Once Foundational is done:
   - Developer A: User Story 1 (calculation engine)
   - Developer B: User Story 2 (asset/liability CRUD + UI)
   - Developer C: User Story 3 (payments + PDF receipts)
3. Stories integrate independently; Polish phase runs last

---

## Notes

- `[P]` tasks operate on different files with no incomplete dependencies
- `[USn]` label maps each task to its user story for traceability
- Nisab values (gold/silver prices) must be sourced reliably — use a configurable default with an optional external API
- Hawl tracking must use the Islamic lunar calendar (Hijri), not Gregorian
- WCAG 2.1 AA compliance (FR-012, SC-005) is mandatory — do not defer T042
- Commit after each task or logical group; stop at checkpoints to validate story independently
