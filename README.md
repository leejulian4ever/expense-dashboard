# Expense Dashboard

A single-page dashboard that answers one question at a glance: **where is
the money going, and is anything moving in the wrong direction?**

View it live: *(add the Vercel URL here once deployed)*

> **Note:** the data behind this dashboard is sample/exercise data used for
> a training project, not live company financials.

## What's on the page

- **Verdict strip** — total spend for the latest month, how that compares to
  the month before (with a plain-language "Better / Worse" call, not just a
  number), and the fastest-growing expense category.
- **Monthly spend trend** — total spend over time, with the fastest-growing
  category's own trend line overlaid so you can see what's driving recent
  changes.
- **Spend by category** — a bar chart ranked largest to smallest.
- **Data quality notes** — anything a viewer should be skeptical of: expenses
  missing a dollar amount, expenses flagged as unverified (e.g. "reimbursed?",
  "check w/ finance"), and possible duplicate charges. These are called out
  up front rather than left for someone to notice on their own.
- **Full expense table** — every row, filterable by category and month,
  sortable by amount.

## How it was built

This dashboard was built by directing [Claude Code](https://claude.com/claude-code)
— describing the questions the dashboard needed to answer and the design
standard to hold to, reviewing what it produced, and asking for specific
changes (chart styling, the data-quality checks, this README) over several
rounds. No hand-written code.

## How it works

It's a single self-contained HTML file — no server, no database, no build
step. The expense data is embedded directly in the page, and all the
numbers, charts, and the data-quality checks are computed in the browser
from that embedded data. That's what makes it possible to host as a static
file on Vercel with nothing else running behind it.

## How the data gets refreshed

The data isn't live-connected to any source system — it's a point-in-time
snapshot embedded in the page, dated by the "Data through [month]" line near
the top. To bring it forward to a new month, the embedded data block is
swapped for an updated export and the site is redeployed. That process is
documented for maintainers in this repo (see the internal refresh notes,
not included in this public copy) — in practice it takes a couple of
minutes and doesn't require writing any code.
