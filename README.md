# Nodeskio IMS

**Offline-first inventory and warehouse control for small retail teams, stockrooms, and light warehouses.**

Nodeskio IMS is a desktop inventory management app built for operators who need dependable local workflows without the cost and complexity of a full cloud ERP. It combines product catalog management, sales, purchase orders, returns, stock counts, warehouse locations, lot/serial traceability, and reporting in a single macOS desktop application.

This repository hosts the public release builds. The source code is maintained privately.

## Download

Latest release: [Nodeskio IMS v0.3.0](https://github.com/utyagi005/IMS-Releases/releases/latest)

Current macOS build:

- [Nodeskio-IMS-0.3.0-arm64.dmg](https://github.com/utyagi005/IMS-Releases/releases/download/v0.3.0/Nodeskio-IMS-0.3.0-arm64.dmg) for Apple Silicon Macs

Packaging note: the macOS app is signed with an Apple Development identity. Notarization is not configured yet, so macOS Gatekeeper may require manual approval on first launch.

## Product Thesis

Inventory software for small businesses often splits into two bad options: spreadsheets that lose traceability, or enterprise systems that are too expensive and heavy for the team actually using them. Nodeskio IMS is designed for the middle ground: a local-first, operator-friendly inventory system that gives small teams warehouse-grade controls without forcing them into a cloud ERP rollout.

The app is built around practical workflows:

- Know what is in stock, where it is, and whether it is sellable.
- Receive purchase orders into locations and bins.
- Transfer stock between locations with in-transit tracking.
- Sell products while preserving margin, lot, and serial history.
- Handle returns without accidentally restocking damaged or over-returned items.
- Count inventory, approve variances, and maintain an audit trail.
- Generate labels, exports, and reports for day-to-day operations.

## Current Capabilities

### Inventory and Warehouse Control

- Product catalog with SKUs, barcodes, categories, suppliers, costs, prices, reorder levels, and planning fields.
- Location and bin-level stock balances.
- Default migration path from simple product quantities into `MAIN / DEFAULT` stock balances.
- Transfer orders with draft, sent, partially received, received, and cancelled states.
- In-transit inventory tracking for stock moving between locations.
- Location-aware product filtering and inventory reporting.

### Sales, Returns, and Purchasing

- Multi-line sales with customer selection and printable receipt output.
- Sale-time cost snapshots for historical margin accuracy.
- Purchase orders with partial receiving, target location/bin receiving, and received-cost updates.
- Sales returns linked to the original invoice and sale item.
- Return quantity validation to prevent returning more than was originally sold.
- Return dispositions for restock, damaged, quarantine, vendor return, and credit-only outcomes.

### Traceability

- Product tracking modes: none, lot, and serial.
- FEFO allocation for lot-tracked sales.
- Lot balances by product, location, bin, and lot.
- Serial status tracking across receiving, sales, returns, transfers, and damaged outcomes.
- Trace search for lots and serial numbers.
- Expiry and value-at-risk reporting for expiring stock.

### Operations and Reporting

- Stock count sessions with expected/count quantities and admin approval for adjustments.
- Replenishment suggestions using sales velocity, lead time, safety stock, target stock, and on-order quantities.
- Transfer-before-purchase suggestions when another location has available stock.
- Barcode and QR label generation.
- CSV and XLSX exports.
- Reports for inventory, low stock, sales, movements, profit, valuation, gross margin, sell-through, dead stock, ABC, reorder, count variance, location inventory, transfers, returns, customers, traceability, expiry risk, user activity, and location margin.

### Audit, Backup, and Local Reliability

- Local SQLite database for offline desktop operation.
- Admin and staff roles with protected backend actions.
- Audit log for key mutations, exports, settings changes, migrations, receiving, transfers, returns, and stock adjustments.
- Backup creation, validation, and restore flow.
- Production Electron packaging with GitHub Release update metadata.

## Technical Snapshot

Nodeskio IMS is built as a modern desktop application:

- Electron desktop shell.
- React renderer.
- TypeScript across app layers.
- SQLite via `better-sqlite3`.
- Playwright-based Electron end-to-end tests.
- Electron Builder release packaging.
- GitHub Releases distribution channel.

The current release was validated with:

- `npm run format:check`
- `npm run typecheck`
- `npm run lint`
- `npm run build`
- `npm run test:e2e` with 12/12 passing
- Temp-home E2E retry to verify isolated test databases
- Electron-runtime migration smoke test for SQLite/native module compatibility
- Local macOS code-signature verification of the packaged app

## Why This Matters

Nodeskio IMS demonstrates the execution path from product concept to shipped desktop software:

- Domain modeling for inventory, locations, lots, serials, returns, transfers, and reporting.
- Local-first architecture for teams that need reliability even without internet access.
- Migration discipline for evolving a database-backed desktop app.
- Practical QA around real workflows rather than only happy-path UI checks.
- A release pipeline that produces downloadable macOS artifacts and updater metadata.

For recruiters, this project shows full-stack desktop product development: UI, data modeling, business rules, native packaging, release management, and automated testing.

For investors or product partners, it represents a focused wedge into small-business inventory operations: a simpler alternative to spreadsheets, with a path toward richer workflows, cloud sync, team collaboration, and vertical-specific editions.

## Roadmap Direction

Near-term product opportunities:

- macOS notarization for smoother first launch.
- Windows builds.
- Cloud backup/sync option while preserving offline operation.
- More polished dashboard analytics and guided onboarding.
- Role-based permissions beyond admin/staff.
- Scanner-first workflows for receiving, stock counts, and transfers.
- Optional hosted data layer for multi-device teams.

## Repository Purpose

This public repository is intentionally small. It is used for:

- Public release notes.
- Downloadable installer assets.
- Auto-update metadata.
- A product-facing overview of Nodeskio IMS.

The private development repository contains the application source, tests, and build pipeline.
