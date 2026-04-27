# Timeline

## Phase 1 — Discovery & Reports Remediation (Week 1)
- Review the existing codebase, data model, and current Reports page behavior.
- Identify the reported defects in the Reports module and confirm the exact filter and i18n gaps.
- Fix frontend filter wiring, backend report data normalization, and any inconsistent label handling.
- Deliver a stabilized Reports page and a short remediation report.

## Phase 2 — Restocking Recommendations (Week 2)
- Define the Restocking requirements with Meridian stakeholders and confirm the budget ceiling input model.
- Implement the new Restocking view in the frontend.
- Add a backend `/api/restocking` endpoint that uses inventory and demand forecast data to recommend purchase order quantities.
- Validate recommendations with sample warehouse scenarios.

## Phase 3 — Automated Browser Testing & Documentation (Week 3)
- Add Playwright browser tests for critical flows, including Reports filtering, locale switching, and Restocking recommendation generation.
- Coordinate with Meridian IT to validate test coverage expectations.
- Produce current-state architecture documentation for the frontend, backend, API, and data model.
- Deliver the final package: code changes, test coverage report, and architecture overview.

## Optional Phase 4 — Desired Enhancements (Week 4)
- If Meridian chooses, extend the engagement to include one or more desired items:
  - UI modernization
  - expanded internationalization support
  - operator-selectable dark mode
- Estimate and scope these enhancements separately after the required work is complete.
