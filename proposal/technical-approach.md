# Technical Approach

## Understanding Meridian’s needs
Meridian needs a stable inventory dashboard that can be safely extended and maintained. The highest priorities are fixing the existing Reports experience, adding Restocking recommendations, and establishing test coverage so IT can approve future changes.

## How we will address the required scope

### R1 — Reports module remediation
- Audit the current `Reports.vue` page and identify all broken filter paths, missing internationalization keys, and inconsistent API payloads.
- Correct filter wiring in the frontend and ensure query parameters are translated consistently through `client/src/api.js` to the backend.
- Update the backend Reports endpoint(s) to normalize data patterns and return consistent labels and values for all supported warehouses and categories.
- Validate behavior with manual checks plus browser tests to ensure filters, sorting, and report outputs behave predictably across locales.

### R2 — Restocking recommendations
- Add a new `Restocking` view under `client/src/views/` with a UI for selecting warehouse, budget ceiling, and review criteria.
- Build a recommendation engine in the backend that uses current inventory, demand forecasts, and budget constraints to propose purchase order quantities.
- Keep the logic transparent: show current stock, forecast demand, recommended order quantity, and expected post-order inventory.
- Use the existing JSON data model in `server/data/` and extend the API with a dedicated `/api/restocking` endpoint.

### R3 — Automated browser testing
- Establish end-to-end coverage using Playwright against the running frontend at `localhost:3000` and backend at `localhost:8001`.
- Focus on critical flows: Reports filtering, locale switching, Restocking recommendation generation, and the core dashboard load path.
- Store tests in `tests/e2e/` and integrate them with the repository’s existing test conventions.

### R4 — Architecture documentation
- Produce a current-state architecture overview that covers:
  - frontend stack and routing
  - backend stack and API surface
  - data sources and JSON-based mock persistence
  - key integration points and deployment ports
- Deliver the overview as a concise written document and optionally as a diagram in `proposal/architecture.html`.

## Assumptions
- The existing application can continue to use the current Vue 3 + Python FastAPI architecture.
- The Restocking view can be implemented with the current JSON-based backend without requiring a database.
- Meridian IT expects browser-level regression coverage for at least the main dashboard/reporting flows before approving production changes.

## Optional desired items
- We recommend treating UI modernization, extended i18n, and dark mode as separate enhancement phases to avoid expanding the initial remediation scope.
- If Meridian prefers a more polished handoff, we can include a targeted UI refresh and broader locale support after the core required work is stable.
