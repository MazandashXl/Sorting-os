# SORTING OS

**Repository description (GitHub):** Offline-first Windows desktop ERP for fruit-sorting operations, including intake, weighing, sorting, inventory, sales, settlements, bank/check workflows, and Persian financial reporting with Rial/Toman support.

SORTING OS is intended for a real fruit-sorting business. It must preserve operational traceability and financial integrity; visual screens without working data paths do not count as implemented features.

## Current repository status

This repository contains an engineering baseline and a staged implementation plan, not a certified production accounting product. The desktop MVP currently includes a Persian Tkinter interface, local SQLite persistence, basic party/shipment/weighing/invoice workflows, and an accounting-core prototype. Its 17 unit tests passed in the package build environment; this is not proof of Windows 7 compatibility, end-to-end operational completeness, or statutory accounting compliance. See `contracts/CURRENT_IMPLEMENTATION_STATUS_FA.md` and `desktop/VALIDATION_REPORT_FA.md`.

## Non-negotiable financial rules

- Store monetary values as integer Rial internally unless a formally approved migration decision says otherwise.
- Convert Toman to Rial exactly using 10 Rial per Toman; never use binary floating-point for money.
- Show the selected unit clearly on every entry and report. A display-unit change must not mutate stored amounts.
- Posted journal entries must balance debit and credit. Corrections must be traceable reversals/adjustments, not silent deletion.
- Financial statements must be calculated from validated posted ledger data, not mock values or invoice status labels.
- Operational events must post to accounting only through explicit, tested business rules.

## Start here

1. Read `START_HERE_FA.md`.
2. Read `docs/agent-system/UPLOAD_FIRST_ORDER_FA.md`.
3. Read `docs/agent-system/SOURCE_OF_TRUTH_AND_CONFLICT_ORDER_FA.md`.
4. Confirm the target repository and branch before making changes.
5. Run only Prompt 00 from `prompts/`. Stop and review its report before Prompt 01.

## Repository map

- `desktop/` — executable Python desktop baseline and tests.
- `docs/` — requirements, workflows, data model, architecture, finance, reporting, security and release rules.
- `prompts/` — ordered AI coding-agent prompts 00–35.
- `contracts/` — traceability, invariants, decisions, implementation status and release gates.
- `reference-inputs/` — source documents retained for reconciliation; they are not automatically higher authority than the conflict-order policy.
- `.github/` — issue, PR and test workflow templates.

## Suggested workflow

Use small, reviewable commits and a feature branch. The agent must report changed files, tests actually run, test results, unresolved questions, and evidence. Never claim a feature is complete because a page or button exists.
