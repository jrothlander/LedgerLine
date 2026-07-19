# Changelog

All notable changes to Ledgerline.

## v13
- Month dropdowns (Dashboard, Transactions, This Month) now list newest month first.

## v12
- **Month in Review**: the This Month tab gained a month selector. Past months render with the same layout but final verdicts — finished over/under budget, "didn't post" bill status, final category results vs. that month's own trailing average, and a "How the month closed" summary. History comparisons are relative to the month being reviewed.

## v11
- **Budgets as % of income**: new percentage column, editable expected income on the Income row (falls back to 3-month actual average), totals row, and an allocation-vs-income bar with an over-100% warning and unallocated-money nudge.

## v10
- **Debt Plan tab**: editable debts (balance, APR, minimum), extra-payment input with a hint from actual payment history, snowball vs. avalanche simulated side by side (debt-free dates, total interest, payoff order), verdict summary, balance-over-time chart, and a non-viable-minimums warning.

## v9
- **Stronger duplicate detection**: optional bank Transaction ID column for definitive dedup; fingerprint matching now counts copies so two genuine identical same-day purchases both import while overlapping re-downloads skip cleanly.

## v8
- **Spending by category on This Month**: collapsible per-category envelopes with budget bars, purchases-so-far, history-based "likely more" projections, a mid-month "projected over" flag, and full transaction lists.

## v7
- Transactions page layout cleanup: single ＋ action menu per row (rule/bill), narrower month column, tighter table paddings, truncated account names.

## v6
- **"+ bill" from any transaction**: track a payment as a monthly bill using its amount and date, with exact-, case-, and overlap-duplicate protection.

## v5
- **This Month tab**: month progress and spending pace, automatic recurring-bill detection (paid / due / expected-check status, median expected amounts), manual bills, hide/restore, and an "after the bills" flexible-money summary.

## v4
- **Paycheck timing**: optionally count income dated on/after a chosen day toward the next month's budget; per-transaction budget-month overrides with visible badges.

## v3
- Visible version stamp in the header.

## v2
- **Rule manager**: inline editing, reordering (first match wins) with send-to-top, add-rule form, duplicate blocking (case/whitespace-insensitive), a rule tester showing which rule wins and what else matched, apply-to-uncategorized and re-run-on-all actions, and one-time cleanup of stored duplicate rules.

## v1
- Initial release: accounts, CSV import with per-account column mapping and duplicate skipping, seeded categorization rules, categories with budgets and kinds (spending/income/savings/investing/debt/transfer), statement-style dashboard with charts, Plan insights, and JSON backup/restore.
