# Ledgerline

**A private, single-file personal budgeting app that runs entirely in your browser.**

Ledgerline replaces the monthly spreadsheet ritual. Import CSV files from your bank accounts and brokerages, let the rules engine categorize transactions automatically, and get a clear picture of your spending, savings, bills, and debt payoff — all in one HTML file, with no server, no account, and no data ever leaving your computer.

## Why Ledgerline

Most budgeting tools want your bank login, a subscription, or your data on their servers. Ledgerline asks for none of that. It is one `.html` file. You download it, double-click it, and everything — transactions, categories, rules, budgets — lives in your own browser's local storage on your own machine.

## Features

- **CSV import with column mapping** — Works with exports from virtually any bank or brokerage. Auto-detects date, description, and amount columns (including separate debit/credit layouts), remembers each account's format, and safely skips duplicates on overlapping date-range re-downloads.
- **Rules-based auto-categorization** — Ships with ~60 starter rules (grocery chains, gas stations, streaming services, payroll). Add your own from any transaction in two clicks. Rules are editable, reorderable (first match wins), duplicate-protected, and testable against sample descriptions.
- **Dashboard** — A statement-style monthly summary: income, spending, saved, invested, debt paid, and what's left over, plus budget bars with overspend flags, a category breakdown chart, and a six-month trend.
- **This Month / Month in Review** — A live view of the current month: progress and pace vs. budget, a bills tracker that learns your recurring bills from history (paid / due / didn't-post status, expected amounts and dates), per-category envelopes with transaction lists and history-based projections, and a "flexible money after upcoming bills" bottom line. Flip the month selector to review any past month with the same layout.
- **Budgets as percentages of income** — Every category budget shown as a slice of your expected income, with a total that warns when you budget past 100%.
- **Paycheck timing** — Paid on the 15th and 30th? Optionally count end-of-month income toward the next month's budget, with per-transaction overrides.
- **Debt payoff planner** — Enter balances, APRs, and minimums; compare the snowball and avalanche strategies side by side: debt-free dates, total interest, payoff order, and a balance-over-time chart.
- **Plan** — Data-driven insights from your recent months: overspending, savings rate vs. target, your biggest spending levers, and subscription totals.
- **Backup & restore** — One-click JSON export/import of everything.

## Quick start

1. Download `home-budget.html` (or clone this repository).
2. Open the file in any modern browser (Chrome, Edge, Firefox, Safari).
3. Go to **Accounts & Backup** and add your accounts (checking, savings, investments).
4. Go to **Import**, pick an account, and drop in a CSV downloaded from your bank.
5. Visit **Transactions** to fix any categories the rules missed — and turn your fixes into rules so next month is automatic.
6. Set your income and budgets on **Budgets & Categories**, then explore the **Dashboard** and **This Month** tabs.

The full walkthrough is in [docs/USER_GUIDE.md](docs/USER_GUIDE.md).

### Hosting it for others

Because Ledgerline is a static file, you can serve it with GitHub Pages: enable Pages on this repository and anyone can use the app at your Pages URL without downloading anything. Each visitor's data stays in *their* browser — the page is served, but nothing is ever sent back.

## Privacy model

- All data is stored in the browser's `localStorage`, scoped to the file/URL you opened.
- The app makes no network calls with your data. The only remote requests are for two public libraries (PapaParse for CSV parsing, Chart.js for charts) and web fonts from CDNs.
- Clearing your browser data erases the app's data — use **Accounts & Backup → Export** to keep backup files.

## Tech

Plain HTML, CSS, and JavaScript in a single file. No build step, no framework, no dependencies to install. [PapaParse](https://www.papaparse.com/) and [Chart.js](https://www.chartjs.org/) are loaded from cdnjs.

## Contributing

Ideas, bug reports, and pull requests are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md) for how the code is organized and how to test changes. If you use a bank whose CSV format doesn't import cleanly, an issue with the column headers (never real transaction data) is especially helpful.

## Disclaimer

Ledgerline is an educational budgeting tool, not financial advice. Payoff simulations and projections are simplified models of your data.

## License

[MIT](LICENSE) — free to use, modify, and share.
