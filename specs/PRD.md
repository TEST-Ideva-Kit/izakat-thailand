# Product Requirements Document (PRD) – iZakat Web Application

## 1. Problem Statement
### Current situation
Many Muslims who follow the Shafi'i fiqh struggle to organize, calculate, and fulfill zakat accurately. Current methods (manual spreadsheets, scattered notes, generic calculators) fail to reflect Shafi'i jurisprudence nuances. There is no centralized platform to track diverse zakat categories, determine nisab with reliable exchange rates, apply deductions, schedule reminders, and securely record fulfillment actions. This leads to inconsistent calculations, missed due dates, and reduced confidence.

### User pain points
- Difficulty categorizing wealth across multiple assets/currencies per Shafi'i rules  
- Uncertainty about nisab thresholds for the current year  
- Need to track debts/living expenses correctly for hawl (lunar year) calculations  
- Lack of automated reminders and jurisprudence-based guidance  
- Inability to generate auditable reports or export receipts  
- Concerns about storing sensitive financial data online  

### Business impact
- High demand among Muslims seeking accurate Shafi'i-aligned zakat management  
- Opportunity to establish a trusted, scalable platform with jurisprudence-aligned features  
- Monetization potential via premium features (reporting, family accounts, partnerships)  
- Improved trust through auditable records and clear explanations  

---

## 2. Proposed Solution
iZakat is a web-based application providing:
- Jurisprudence-driven calculation engine  
- Asset/liability tracking with multi-currency support  
- Nisab calculation using up-to-date exchange rates  
- Deductions for debts and essential expenses  
- Automated reminders for zakat due dates  
- Auditable reports, receipts, and export capabilities  

### User stories
- Create a personalized profile aligned with Shafi'i jurisprudence  
- Input/categorize assets and liabilities with validation/currency support  
- Automatic zakat calculation with deductions per Shafi'i rules  
- Nisab calculated via gold/silver/cash equivalents  
- Configurable reminders (email, push, SMS)  
- Detailed calculation reports with breakdowns  
- Record zakat payments and attach receipts  
- Export/import data (PDF/CSV)  
- Guidance and FAQs with scholarly disclaimers  
- Multi-language and WCAG-compliant accessibility  

### Success metrics
- Activation rate (profile setup within 14 days)  
- MAU/DAU retention cohorts (3/6/12 months)  
- Calculation accuracy (&gt;95% QA pass rate)  
- On-time zakat fulfillments (±7 days window)  
- User satisfaction (NPS, qualitative feedback)  
- Data portability/auditability (reports/receipts per quarter)  

---

## 3. Requirements
### Functional
- **User Management**: registration, login, 2FA, profiles, role-based access  
- **Asset/Liability Management**: categories (cash, gold, investments, business assets, etc.), debts, multi-currency support  
- **Zakat Engine**: compute zakatable wealth, apply nisab thresholds, hawl tracking, 2.5% rate, category breakdowns  
- **Reminders/Notifications**: schedule, email/SMS/in-app, customizable cadence  
- **Reporting/Export**: breakdowns, receipts, PDF/CSV export  
- **Guidance/Content**: Shafi'i explanations, FAQs, disclaimers  
- **Security/Compliance**: encryption, audit logs, GDPR-like compliance  
- **Design/Accessibility**: responsive UI, localization, WCAG AA compliance  

### Technical
- **Architecture**: modular web app, API-first design  
- **Frontend**: React + Next.js  
- **Backend**: Node.js/Express or Python FastAPI  
- **Database**: PostgreSQL, Redis  
- **Security**: OAuth2/OpenID Connect, RBAC, MFA  
- **Observability**: logging, metrics, error tracking  
- **Deployment**: CI/CD, Docker, Kubernetes  
- **Integrations**: currency feeds, email/SMS, optional payment gateway  
- **Performance**: caching, background jobs, backups  
- **Privacy**: consent management, audit trails  

### Design
- Onboarding flow, dashboard, step-by-step forms  
- Transparent breakdowns, printable/exportable reports  
- WCAG compliance, localization, branding consistency  

---

## 4. Implementation
### Dependencies
- Internal: PM, Engineering, Security, Design, QA, Content  
- External: hosting, currency provider, email/SMS, payment gateway, analytics  

### Timeline
- **Phase 1 (2–3 weeks)**: discovery, architecture, scope, mockups  
- **Phase 2 (10–14 weeks)**: MVP (profiles, assets/liabilities, zakat engine, reminders, reporting, localization, security)  
- **Phase 3 (4 weeks)**: beta, feedback, refinements  
- **Phase 4 (2 weeks)**: general availability, marketing, support  

### Resources
- 1 PM, 2–3 frontend engineers, 2 backend engineers, 1 DevOps/SRE  
- 1 designer, 1–2 QA engineers, 1 content specialist, 1 support advocate  

---

## 5. Risks &amp; Mitigations
- **Incorrect calculations** → rules engine, scholarly citations, disclaimers, automated tests  
- **Inaccurate nisab values** → reputable feeds, cached historical rates, user choice of reference  
- **Data privacy/security** → encryption, access controls, compliance reviews  
- **Adoption challenges** → strong onboarding, quick wins, feedback loops  
- **External dependencies** → redundancy, SLAs, fallback behaviors  
- **Scope creep** → tightly scoped MVP, change control, backlog prioritization  

---
**Note:** This PRD emphasizes accuracy, compliance, usability, and auditable records to build trust among users following Shafi'i jurisprudence.