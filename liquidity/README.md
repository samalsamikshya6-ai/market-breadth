# Liquidity Map

Market → Sector → Industry → Stock, read through turnover and delivery
rather than price.

- `index.html` — the current session. Overwritten by the nightly job.
- `archive/YYYY-MM-DD.html` — one self-contained file per session.

Each file is standalone: open it in a browser, no server needed.

## Source data

| What | Where |
|---|---|
| Turnover, delivery, breadth | NSE full securities bhavcopy (`sec_bhavdata_full_DDMMYYYY.csv`) |
| Index levels and changes | NSE official `ind_close_all_DDMMYYYY.csv` |
| Sector classification | Nifty Total Market / Microcap 250 / Nifty 500 constituent files |
| Industry classification | NSE four-tier classification, per stock |
| F&O membership | NSE `fo_mktlots.csv` |

Index figures come from the official end-of-day file, never the live API,
which still returns intraday values in the evening.

## Reading it

**Flow** is a group's share of the latest session's turnover minus its share
across the 21-session month. Positive means liquidity expanding into it.

**Deliv %** is turnover-weighted, and is coloured against the selected
segment's own average — F&O and cash-only names have very different
baselines (about 51% against 34%), so one market-wide number would mislead.

**× avg** marks a stock trading at twice its own prior five-session average
turnover or more. Read it next to delivery: a high multiple with collapsed
delivery is churn, not accumulation.

For research. Not investment advice.
