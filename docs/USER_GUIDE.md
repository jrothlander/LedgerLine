# Ledgerline User Guide

This guide walks through every tab and the monthly workflow. Ledgerline is a single HTML file; open it in your browser and everything below happens locally on your machine.

## First-time setup

**1. Add your accounts.** On **Accounts & Backup**, create one entry per real-world account — each checking account, savings, brokerage, 401k. The account type (checking / savings / investment / debt) is descriptive; what matters for the numbers is transaction categorization.

**2. Set your income and budgets.** On **Budgets & Categories**, enter your expected monthly take-home income in the **Income** row's budget field. Then set monthly budgets on the categories you care about. The **% of income** column shows each budget as a slice of income, and the totals row keeps you honest: spending + savings + investing + debt budgets should never exceed 100% of income, and getting *close* to 100% (every dollar assigned a job) is the actual goal.

**3. Check the category types.** Each category has a type that controls how it counts: **spending**, **income**, **savings**, **investing**, **debt payment**, or **transfer**. Transfers are ignored entirely — categorize movements between your own accounts as Transfer so they never double-count.

## The monthly workflow

A typical session takes a few minutes:

1. Download CSVs from each bank/brokerage (overlapping date ranges are fine — duplicates are skipped).
2. **Import** each file to its account.
3. On **Transactions**, filter to "uncategorized only" and fix what the rules missed. Use the row's **＋** menu to turn a fix into a permanent rule, or to track a payment as a monthly bill.
4. Review last month in **This Month → Month in Review** to see how it closed.
5. Check the current month's bills and category envelopes on **This Month**.

## Importing CSVs

Pick the account the file belongs to, then drop the CSV. Ledgerline auto-guesses which columns hold the date, description, and amount — including banks that use separate debit and credit columns — and shows a preview. **Money out should show red**; if the signs are backwards, tick "flip signs." The mapping is remembered per account, so future imports are two clicks.

**Duplicates.** Re-downloading overlapping ranges is safe. Ledgerline recognizes previously imported transactions by your bank's transaction ID when the file has one (map the optional "Transaction ID" column), otherwise by account + date + amount + description with copy-counting — so two genuine identical purchases on the same day both import, while re-downloads skip.

## Transactions

Filter by month, account, or uncategorized-only. Each row lets you:

- **Set the category** from the dropdown.
- **＋ → Create category rule** — any future (or current uncategorized) transaction containing your chosen text gets this category automatically.
- **＋ → Track as monthly bill** — adds the merchant to the This Month bills tracker with the expected amount and day taken from this transaction.
- **Mo.** — override which budget month the transaction counts toward (see Paycheck timing below).

<img width="1062" height="300" alt="image" src="https://github.com/user-attachments/assets/60563b4b-9556-412a-8c75-a164ac496776" />

For these three transactions, I am going to set "Cammies Old Dutch Ice Cream" to the "Dining & Coffee" category. If this is a place I visit often, I am going to check the [+] button and set this as a rule. That way, the next time I visit, the rule will be applied, and it will automatically be categorized as "Dining & Coffee," which is really the main point of the software: to auto-categorize and track your spending. Now, for Packt Publishing, this is a subscription. So I set it to subscriptions and created it as a rule. If for some reason this showed up as on the 30th of the month, but I wanted to apply it to next month's budget, I would select the [auto] dropdown list and select "next", meaning that I want to apply this to next month. Same for if it showed up on the 1st and I wanted to apply to the previous month, I can set it to "prev". This is because some things show up a few days early or late, and you will want to adjust the time to apply it to your budget on a given month.

## Rules

Rules live at the bottom of **Budgets & Categories**. Each rule is "if the description contains X, categorize as Y." They are checked **top to bottom and the first match wins**, so put specific rules (like `ABC MORTGAGE PAYROLL → Income`) above generic ones (like `MORTGAGE → Housing`). This is necessary for me because I work for a mortgage company and I have a mortgage. So it tried to appy my paycheck as a mortgage payment until I added a rule to apply the payroll entry to Income and the Mortgage entry to housing. Use the arrows to reorder, ⤒ to send a rule to the top, and the **Test a description** box to paste a real description and see exactly which rule catches it — including when multiple rules match and order decides.

Duplicate rules are blocked automatically. After editing rules, you can **Apply rules to uncategorized** or **Re-run rules on ALL transactions** (this overwrites manual category choices where a rule matches — it will ask first).

<img width="1113" height="710" alt="image" src="https://github.com/user-attachments/assets/9488096c-ab27-409c-84ea-a4ae658ecc16" />

## This Month / Month in Review

The month selector defaults to the current month; pick any past month for the same page in review mode.

**Current month** shows: month progress and spending pace vs. your total budget; income so far; the **bills tracker**; per-category **envelopes**; and **After the bills** — income so far, minus everything already out, minus expected upcoming bills, equals your flexible remainder.

**Bills tracker.** Ledgerline detects recurring bills automatically: merchants that charge you in at least two of the last three months, about once per month (that once-a-month rhythm is what keeps grocery runs off the list). Each bill shows paid / due ~date / "expected — check" status, the expected amount (median of recent charges), and the day it usually posts. **Hide** removes a merchant from bill treatment permanently — across all months, past and future — without touching the transactions themselves. Bills the detector can't see (brand-new, or inconsistent descriptions) can be added manually here or via "+ bill" on any transaction.

**Category envelopes.** Every spending category gets a collapsible section: budget bar, purchases so far, what's left, and a history-based projection ("usually ≈$180/mo across 4 purchases → ≈$90 more likely"). A **projected over** flag warns mid-month when the likely remainder won't fit the budget. Click a category to see its transaction list.

**Month in Review** keeps the identical layout but reports finals: "finished over/under" instead of pace, "didn't post" for bills that never arrived that month, final spend vs. budget vs. that month's own trailing average, and "How the month closed" — the full income-minus-everything arithmetic. History comparisons are always relative to the month being reviewed, so a June review compares June to March–May.

## Paycheck timing

If a paycheck around the 30th really funds *next* month: on **Budgets & Categories → Income timing**, enable "count income dated on or after day N toward the next month" (25 is a good default for a paycheck due on the 30th that sometimes lands early). It applies to Income-categorized transactions only, including already-imported ones. Override any individual transaction with the **Mo.** control on Transactions — handy for the paycheck that lands oddly, or rent paid on the 31st for next month.

<img width="1038" height="160" alt="image" src="https://github.com/user-attachments/assets/e151e1bc-e01c-48aa-8907-98fdf4254009" />

## Debt Plan

Enter each debt's balance, APR, and minimum payment, plus how much extra you can pay monthly (the app hints at a realistic number from your actual Debt Payment transactions). Two strategies are simulated side by side:

- **Snowball** — extra money attacks the smallest balance first; each payoff frees its minimum for the next debt. Earliest first win.
- **Avalanche** — extra attacks the highest APR first. Mathematically cheapest.

You'll see debt-free dates, total interest, per-debt payoff order, the dollar value of your extra payment vs. minimums-only, and a balance-over-time chart. Balances are a snapshot you enter — update them monthly from your statements. If a minimum payment doesn't cover a debt's monthly interest, the app flags that the plan never finishes rather than showing misleading numbers.

<img width="1061" height="830" alt="image" src="https://github.com/user-attachments/assets/848b17ab-aa60-4fe5-928f-4bb0c8cb9513" />

## Plan

Automatic insights from your recent months: categories over budget and by how much, your savings rate vs. your target (default 20%), your three biggest spending levers with what a 10% trim frees up, subscription totals, and debt-payment framing.

<img width="1067" height="704" alt="image" src="https://github.com/user-attachments/assets/84dc0046-98c4-43e8-911f-1703394e0122" />

## Backup, restore, and data

Everything lives in your browser's local storage, keyed to the file/URL you opened. That means:

- **Export a backup** (Accounts & Backup → Export) after each monthly session. Restoring a backup replaces current data.
- Clearing browser site data erases the app's data.
- Opening the HTML file from a *different location* (or a hosted URL vs. a local file) is a different storage bucket — your data doesn't follow the file, so keep opening the same copy, and move between copies via backup files.
- Replacing the HTML file with a newer version in the same location keeps your data.

## FAQ

**Is anything uploaded anywhere?** No. The app makes no network calls with your data; only the charting/CSV libraries and fonts load from CDNs.

**My paycheck got categorized as Housing because my employer's name contains "Mortgage."** Rule order: add a specific rule for your payroll description pointing to Income; new rules go to the top and win. Then "Re-run rules on ALL transactions" to fix history.

**A bill shows "didn't post" but I paid it.** Its description may have changed (bank processor changes are the usual culprit), so the fingerprint no longer matches — check Transactions for the charge and consider a manual bill with broader match text.

**Can I use it on my phone?** It's designed for desktop browsers. The file will open on mobile, but the tables are desktop-oriented.
