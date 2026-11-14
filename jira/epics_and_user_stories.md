# Agile Delivery Plan — Epics & User Stories
## Ratna Sweets — Festival Demand & Freshness Management System

> Note: This backlog is a simulated planning artifact for this portfolio case study, written as if produced by the BA in collaboration with the Dev team and Product Owner (Business Owner persona).

---

## Epic 1 — Demand Forecasting Engine
*Covers FR-01, FR-02*

**US-01**: As a Production Manager, I want the system to generate a festival demand forecast per outlet using historical sales data, so that I can plan production quantities in advance instead of relying on guesswork.
- AC1: Forecast is generated per outlet, per product category, at least 10 days before a tagged festival window.
- AC2: Forecast uses at least 2 years of historical sales data where available.
- AC3: Forecast accuracy (MAPE) is visible to the Production Manager alongside the number.

**US-02**: As a Sales Manager, I want to see the consolidated demand forecast across all outlets, so that I can validate it against ground-level knowledge (e.g., known bulk/corporate orders) before production is finalized.
- AC1: Consolidated forecast view is accessible to Sales Manager role.
- AC2: Sales Manager can flag a forecast line as "needs review" with a comment.

---

## Epic 2 — Production Planning Integration
*Covers FR-03*

**US-03**: As a Production Manager, I want the system to recommend production quantities based on the forecast and confirmed bulk orders, so that I don't have to manually reconcile multiple data sources.
- AC1: Recommended quantity = forecast + confirmed bulk orders − current finished-goods stock.
- AC2: Production Manager can override the recommended quantity with a mandatory reason field.
- AC3: Final production plan is timestamped and logged for audit.

**US-04**: As a Procurement Manager, I want to receive consolidated raw material requirements derived from the production plan, so that I can place supplier orders early enough to avoid festival-season shortages.
- AC1: Raw material requirement list auto-generates once production plan is finalized.
- AC2: List breaks down requirements by raw material and required-by date.

---

## Epic 3 — Real-Time Batch Inventory & Expiry Tracking
*Covers FR-04, FR-05*

**US-05**: As an Inventory Manager, I want every production batch tagged with a manufacture date and shelf-life-based expiry date, so that freshness can be tracked automatically rather than by manual spot checks.
- AC1: Every batch record includes batch ID, product, manufacture date, expiry date, quantity, and current outlet location.
- AC2: Shelf-life rules are configurable per product category.

**US-06**: As a Store Manager, I want to see real-time batch-level stock and expiry status for my outlet, so that I can act before stock expires rather than after.
- AC1: Dashboard shows days-to-expiry per batch, sorted by urgency.
- AC2: Data refresh interval is no more than 1 hour during festival windows.

---

## Epic 4 — Automated Discount/Transfer Recommendations
*Covers FR-06*

**US-07**: As the system, I want to flag a batch as "near-expiry risk" when it crosses a configurable threshold (e.g., <3 days to expiry with >20% stock remaining), so that outlets are alerted before waste occurs.
- AC1: Threshold is configurable by Business Owner / Admin role.
- AC2: Alert is generated within 1 hour of a batch crossing the threshold.

**US-08**: As a Store Manager, I want the system to recommend either a discount or an inter-outlet transfer for near-expiry stock, so that I can act on a clear recommendation instead of deciding from scratch.
- AC1: Recommendation logic considers stock levels at nearby outlets before suggesting a transfer.
- AC2: Store Manager can approve, modify, or dismiss the recommendation, with the action logged.

**US-09**: As a Store Manager, I want to see a stockout-risk alert when an outlet is projected to run out of a product before the festival ends, so that I can request rebalancing proactively.
- AC1: Stockout projection uses current sell-through rate vs remaining stock.
- AC2: Alert includes a suggested source outlet for rebalancing, where available.

---

## Epic 5 — Finance & Owner Dashboard
*Covers FR-07*

**US-10**: As the Business Owner, I want a consolidated dashboard showing wastage cost, fulfilment rate, and other KPIs across all outlets, so that I can evaluate festival performance without waiting for manual reports.
- AC1: Dashboard includes at minimum: wastage cost, fulfilment rate, forecast accuracy, stockout incidents.
- AC2: Dashboard data is viewable by festival window (e.g., Diwali 2026) for year-over-year comparison.

**US-11**: As a Finance Manager, I want wastage cost calculated automatically from expired/discounted stock, so that I don't have to manually reconcile inventory write-offs each festival season.
- AC1: Wastage cost = (expired units × unit cost) + (discount amount applied to near-expiry stock sold).
- AC2: Figure is auto-updated daily during the festival window.

---

## Epic 6 — Procurement Sync
*Covers FR-08*

**US-12**: As a Procurement Manager, I want raw material requirements to update automatically if the production plan changes, so that I'm not working off stale numbers.
- AC1: Any change to the finalized production plan triggers a recalculation of raw material needs.
- AC2: Procurement Manager is notified of the change with a before/after delta.

---

## Prioritization Notes
- Epics 1–3 are foundational (forecasting → production → inventory tracking) and must ship first.
- Epic 4 depends on Epic 3 (needs live batch data to detect risk).
- Epic 5 depends on data from Epics 3 and 4 to be meaningful.
- Epic 6 can be developed in parallel with Epic 2.