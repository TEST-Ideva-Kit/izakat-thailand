# Feature Specification: Zakat Calculation and Management

**Feature Branch**: `001-description-yet-project`
**Created**: 2026-06-13
**Status**: Draft
**Input**: User wants to accurately calculate and manage their Zakat obligations according to Shafi'i jurisprudence.

## User Scenarios & Testing *(mandatory)*

<!--
  IMPORTANT: User stories should be PRIORITIZED as user journeys ordered by importance.
  Each user story/journey must be INDEPENDENTLY TESTABLE - meaning if you implement just ONE of them,
  you should still have a viable MVP (Minimum Viable Product) that delivers value.
  
  Assign priorities (P1, P2, P3, etc.) to each story, where P1 is the most critical.
  Think of each story as a standalone slice of functionality that can be:
  - Developed independently
  - Tested independently
  - Deployed independently
  - Demonstrated to users independently
-->

### User Story 1 - Accurately Calculate Zakat Amount (Priority: P1)

As a Muslim following Shafi'i jurisprudence, I want to input my assets and liabilities so that the application can accurately calculate my total Zakat due based on established rules.

**Why this priority**: This is the core value proposition of the application; accurate calculation is paramount for users seeking to fulfill their religious obligations correctly.

**Independent Test**: Users can input a defined set of assets/liabilities and verify the calculated Zakat amount against manual Shafi'i jurisprudence calculations. The system delivers a complete, auditable Zakat calculation.

**Acceptance Scenarios**:

1.  **Given** a user has entered their assets (e.g., cash, gold) and liabilities, **When** they request to calculate Zakat, **Then** the system displays the total Zakat amount due based on Shafi'i rules, including Nisab and Hawl.
2.  **Given** a user has entered assets and liabilities, **When** the Nisab threshold for the current year is not met for a particular asset class, **Then** the Zakat calculation correctly shows zero for that asset class.
3.  **Given** a user has entered cash assets and liabilities, **When** calculating Zakat, **Then** the system accurately accounts for the lunar year (Hawl) for cash assets.

---

### User Story 2 - Track Assets and Liabilities (Priority: P2)

As a user, I want to track various types of assets and liabilities, potentially in different currencies, so that I can provide accurate and comprehensive inputs for Zakat calculations.

**Why this priority**: Accurate calculation relies on comprehensive and correct input data. Tracking assets and liabilities is fundamental to this process.

**Independent Test**: Users can add, edit, and view a list of their assets and liabilities, including their values, currencies, and dates, delivering a structured view of their financial position for Zakat purposes.

**Acceptance Scenarios**:

1.  **Given** a user is on the asset/liability tracking screen, **When** they add a new asset (e.g., gold), **Then** they can specify its type, quantity, currency, and acquisition date.
2.  **Given** a user has multiple assets and liabilities in different currencies, **When** viewing their financial overview, **Then** the system displays these items clearly, with options to see aggregated values or individual details.
3.  **Given** a user has liabilities (debts), **When** entering them, **Then** they can specify the amount, currency, and due date.

---

### User Story 3 - Record Zakat Payment and Generate Receipt (Priority: P3)

As a user, I want to record my Zakat payments and generate a receipt, so that I have an auditable record of fulfillment for my religious obligations.

**Why this priority**: Fulfilling Zakat is a key religious obligation, and users need a record for their own accountability and auditability.

**Independent Test**: Users can mark a calculated Zakat amount as paid and generate a downloadable receipt containing key details, providing a documented record of fulfillment.

**Acceptance Scenarios**:

1.  **Given** a Zakat amount has been calculated, **When** the user marks it as paid, **Then** they can input the payment date and optionally attach a receipt.
2.  **Given** a Zakat payment has been recorded, **When** the user requests a receipt, **Then** a downloadable receipt is generated showing the calculated amount, payment date, and user details.

---

### Edge Cases

*   What are the specific categories of assets and liabilities that must be supported to align with Shafi'i jurisprudence?
*   How should 'essential expenses' be defined and accounted for as deductions in Zakat calculations according to Shafi'i jurisprudence?
*   What is the required level of detail for explanations and scholarly disclaimers regarding Shafi'i jurisprudence principles within the application?

## Requirements *(mandatory)*

<!--
  ACTION REQUIRED: The content in this section represents placeholders.
  Fill them out with the right functional requirements.
-->

### Functional Requirements

*   **FR-001**: System MUST allow users to create and manage a profile, including basic personal information and settings relevant to Shafi'i jurisprudence.
*   **FR-002**: System MUST allow users to add, edit, and categorize various types of assets (e.g., cash, gold, silver, investments, business assets, property) with associated values, currencies, and acquisition dates.
*   **FR-003**: System MUST allow users to add, edit, and categorize liabilities (debts) with associated amounts, currencies, and due dates.
*   **FR-004**: System MUST calculate zakatable wealth by aggregating assets and deducting eligible liabilities according to Shafi'i jurisprudence.
*   **FR-005**: System MUST determine Nisab thresholds for applicable currencies and asset types based on current market data (gold/silver equivalents).
*   **FR-006**: System MUST calculate the Zakat due at the applicable rate (2.5% for wealth) only if the zakatable wealth meets or exceeds the Nisab.
*   **FR-007**: System MUST track the lunar year (Hawl) for applicable asset types, particularly cash.
*   **FR-008**: System MUST provide a detailed breakdown of the Zakat calculation, showing assets, liabilities, Nisab, Hawl, and the final Zakat amount.
*   **FR-009**: System MUST allow users to record completed Zakat payments, including the date of payment and optional notes or receipt attachments.
*   **FR-010**: System MUST generate an auditable Zakat receipt for recorded payments.
*   **FR-011**: System MUST provide clear explanations and guidance on Shafi'i jurisprudence principles related to Zakat calculation.
*   **FR-012**: System MUST adhere to WCAG AA accessibility standards.

### Key Entities *(include if feature involves data)*

*   **User Profile**: Represents an individual user, storing personal details, jurisprudence-specific settings, and preferences.
*   **Asset**: Represents a financial asset owned by the user (e.g., cash, gold, stocks). Key attributes include type, value, currency, acquisition date, and Shafi'i classification.
*   **Liability**: Represents a debt or financial obligation owed by the user. Key attributes include type, amount, currency, and due date.
*   **Zakat Calculation**: Represents a specific instance of Zakat calculation. Key attributes include the calculated amount, date of calculation, breakdown of components (assets, liabilities, Nisab, Hawl), and payment status.

## Success Criteria *(mandatory)*

<!--
  ACTION REQUIRED: Define measurable success criteria.
  These must be technology-agnostic and measurable.
-->

### Measurable Outcomes

*   **SC-001**: Users can accurately calculate their total Zakat amount for a given set of assets and liabilities, with calculation accuracy verified against independent Shafi'i jurisprudence expert calculations for 95% of test cases.
*   **SC-002**: The system correctly applies Shafi'i jurisprudence rules for asset categorization, Nisab threshold determination (based on gold/silver equivalents), and Hawl calculations, as validated by QA testing.
*   **SC-003**: Users can add and track at least 10 distinct assets and 5 distinct liabilities, with data integrity maintained across different currencies, achieving a data entry completion rate of 90% for new users within 5 minutes.
*   **SC-004**: 90% of calculated Zakat amounts can be successfully generated as auditable receipts in PDF format.
*   **SC-005**: The application achieves WCAG 2.1 AA compliance as verified by an automated accessibility audit tool.

---