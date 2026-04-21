<!--
Sync Impact Report:
- Version change: 1.3 → 1.4
- Modified principles: All sections updated from template to Loan Simulator specifics
- Added sections: All sections customized for Loan Simulator project
- Removed sections: Template placeholder sections
- Templates requiring updates: ✅ All templates will be automatically updated when the constitution is used
-->

# Loan Simulator Constitution

## Core Principles

### API-First Development
Define API contract FIRST before implementation. API specification serves as contract between frontend and backend. Ensures consistency and prevents integration issues. Backend and frontend development can proceed in parallel after contract is defined.

### Separation of Concerns
Backend handles business logic, calculations, data validation. Frontend handles user interface, presentation, user experience. API Layer provides clear contract between frontend and backend.

### Test-Driven Development (TDD) - NON-NEGOTIABLE
TDD mandatory: Tests written first, then implement minimal code to pass. Red-Green-Refactor cycle strictly enforced. Core calculation logic must be 100% tested, all components should have basic rendering and interaction tests.

### Responsive Design
Three-level responsive design (Desktop ≥1024px, Tablet ≥768px, Mobile <768px). On Desktop and Tablet, the loan input form is presented in a persistent left side-panel alongside results; on Mobile, components stack vertically in a single column.

### Documentation Living Standard
The main README.md file must always be kept up to date with current details. README must include shield badges reflecting technologies used. Technology badges, setup instructions, and usage guide must be maintained as project evolves.

## Architecture and Technical Standards

### Component Architecture
Backend follows service-driven architecture with routes, services, models, and tests. Frontend uses component-based architecture with clear separation between UI components, API services, and application management.

### API Contract
 POST /api/calculate-loan endpoint with standardized request/response schema. Request includes amount (number > 0), term (integer months > 0), rate (number 0-100). Response includes monthlyPayment, totalPayment, totalInterest, and installments array with payment breakdown.

### Coding Standards
Code should be self-documenting with clear variable names. Use type annotations/hints for all function signatures. Use precise decimal types for all monetary calculations; avoid floating-point arithmetic. Follow established coding standards throughout.

### Performance Standards
API should respond within 100ms for calculations. Frontend should load within 2 seconds. All monetary calculations accurate to 2 decimal places. Simple interest calculations are lightweight; no optimization needed for PoC.

## Development Workflow

### TDD Methodology
Test-Driven Development following Red-Green-Refactor cycle. Write failing test first, write minimal code to pass the test, improve code while keeping tests green. Backend tests cover calculation accuracy, edge cases, input validation, API endpoints. Frontend tests cover component rendering, user interactions, API integration, result display.

### Version Control Workflow
Use conventional commit messages: feat:, fix:, test:, docs:, refactor:. Main branch contains stable working code. Feature branches for each major component. Commit after each passing test (TDD cycle).

### Security Requirements
Input validation on both client-side and backend. CORS enabled for local development. Never expose internal error details to users. Return appropriate HTTP status codes (200 for success, 400 for validation errors, 500 for server errors). No sensitive data handling beyond calculation inputs.

## Project Constraints

### Scope Limitations
Simple interest only (no compound interest). Monthly payments only with fixed frequency. No database or data persistence. Development mode only, not production-ready. Single user focus with no multi-user support.

### Functional Limitations
No authentication or user accounts. No history saving or retrieval. No comparison of multiple loan scenarios. No charts or graphs. No export functionality.

## Success Criteria

### Functional Success
User can input loan amount, term (months), and interest rate. System calculates and displays monthly payment correctly. System generates complete amortization schedule. Final payment results in $0.00 remaining balance. All calculations are mathematically accurate using simple interest formula.

### Technical Success
Backend API responds successfully to valid requests. Frontend communicates properly with backend. All unit tests pass (backend and frontend). Application runs without errors in development mode. API contract is consistent between frontend and backend.

### Quality Success
Code follows established coding standards. All components have corresponding tests (TDD). Documentation is complete (README files). Input validation works on both frontend and backend. Error messages are clear and user-friendly.

## Governance

Constitution supersedes all other practices. Amendments require documentation, approval, migration plan. All PRs/reviews must verify compliance. Complexity must be justified. Use this constitution for runtime development guidance.

**Version**: 1.4 | **Ratified**: 2026-01-01 | **Last Amended**: 2026-04-21