# Contributing to Ledgerline

Thanks for your interest! Bug reports, feature ideas, bank-compatibility reports, and pull requests are all welcome.

## Reporting issues

- **Bugs**: describe what you did, what you expected, and what happened. Browser name/version helps.
- **CSV import problems**: include your bank's column headers and one or two rows with **fake data** (never real transactions, balances, or account numbers). The header row is usually all that's needed.
- **Feature ideas**: describe the problem you're trying to solve, not just the feature — it often leads to a better design.

## Development

There is no build step. The entire application is `home-budget.html`: CSS in a `<style>` block, JavaScript in a single `<script>` block. Edit the file, refresh the browser. Test with a separate copy of the file (or a different browser profile) so your real budgeting data isn't disturbed — localStorage is keyed to the file location.

### Architecture

The script is organized top to bottom:

| Section | What it does |
|---|---|
| **State & persistence** | `S` is the single state object (accounts, categories, rules, transactions, mappings, bills, debts, settings). `load()`/`save()` round-trip it through `localStorage` under one key, with migrations/defaults applied in `load()`. |
| **Helpers** | Formatting (`fmt`, `fmt0`), escaping (`esc`), date/month math (`parseDate`, `monthKey`, `shiftMonth`, `effMonth`). |
| **Month math** | `computeMonth(mk)` aggregates a budget month: income, spending, savings, investing, debt, leftover, savings rate. `effMonth(t)` decides which budget month a transaction counts toward (calendar month, payday-shift setting, or per-transaction override). |
| **Bills** | `detectBills(mk)` finds recurring monthly charges relative to a given month; `addManualBill` with overlap-blocking. |
| **Debt** | `simulatePayoff(debts, extra, strategy)` — rolling snowball/avalanche simulation. |
| **Budget allocation** | `budgetAllocation()` — budgets as % of expected income. |
| **CSV import** | `guessMapping`, `normalizedRow`, `commitImport` with ID-based and occurrence-counting duplicate detection. |
| **Rendering** | One `rXxx(m)` function per tab, dispatched by `render()`. Views rebuild their DOM wholesale and wire event handlers after. Charts are tracked in `charts[]` and destroyed on re-render. |

### Conventions

- **Amounts are signed**: negative = money out, positive = money in. "Spending" totals are positive numbers derived from `-amount`.
- **Budget months are `'YYYY-MM'` strings**; use `effMonth(t)` (not `monthKey(t.date)`) whenever aggregating, so paycheck timing and overrides are respected.
- **Rules are ordered; first match wins.** Anything that adds rules must go through `addRule` for duplicate protection.
- **Escape all user-derived strings** with `esc()` when building HTML.
- New state must get a default in `load()` so existing users' stored data upgrades cleanly.

### Testing

The engine (everything before the rendering section) is deliberately DOM-light so it can be tested in Node: stub `localStorage`/`document`, `eval` the engine portion of the script, and assert against the pure functions. The upstream development process keeps suites for parsing, rules, month-shift, bills, category detail, dedup, debt simulation, and allocation — if you change engine behavior, please include a small Node test or at least a manual test recipe in your PR description. Always run `node --check` on the extracted script before submitting.

### Pull request guidelines

- Keep the single-file architecture — no build tools, frameworks, or new runtime dependencies without prior discussion in an issue.
- New libraries must load from cdnjs and degrade gracefully offline.
- Preserve backward compatibility with existing localStorage data (add `load()` migrations).
- Match the existing visual style (CSS variables at the top of the file).
- Update `CHANGELOG.md` and, for user-facing changes, `docs/USER_GUIDE.md`.

## Privacy principles (non-negotiable)

Ledgerline's core promise is that financial data never leaves the user's machine. PRs must not add analytics, telemetry, remote logging, or any network transmission of user data.
