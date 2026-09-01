# How ČNB Rates Drive the Czech Mortgage Market

Portfolio data project analysing how the Czech National Bank's policy rate feeds
through to mortgage and consumer-loan rates, the bank spread, and loan volumes.
Data is cleaned and reshaped in Python (pandas) and visualised in an interactive
Power BI dashboard.

## Question

When the central bank changes its policy (repo) rate, how — and how fast — do
mortgage rates and loan volumes react?

## Data

Public time series from the **Czech National Bank (ČNB / ARAD)**, monthly,
2004–2026:
- interest rates and volumes of new housing loans (mortgages) and consumer loans
- 2-week repo rate (the ČNB policy rate)
- household deposits

Source: https://www.cnb.cz/arad/

The three raw exports came in three different shapes (one wide, one transposed,
one event-based), so the first part of the project was cleaning and reshaping
them into one tidy monthly table.

## Tools

- Python: pandas (cleaning, reshaping, joining the sources by month)
- Power BI: data model, DAX measures, dashboard

## Repository contents

- `data_preparation.ipynb` — Python notebook: cleans and merges the three raw exports
- `cnb_merged.csv` — the cleaned, merged monthly dataset (output of the notebook)
- `dashboard.png` — the Power BI dashboard
- `cnb_dashboard.pbix` — the Power BI file
- `data/` — raw ČNB exports (`loans_new_business.csv`, `deposits.csv`, `repo_rate.txt`)

## Key findings

- **Mortgage rates follow the repo rate, but with a lag.** When the ČNB raised
  the repo rate sharply in 2021–2022 (from 0.5% to 7%), mortgage rates rose more
  slowly and never reached the repo level while it was held high.
- **The spread (mortgage rate − repo rate) went negative from late 2021 to
  mid-2024.** For about two and a half years mortgages were cheaper than the
  policy rate. This is real, not a data error: the ČNB held the repo rate at 7%
  for roughly a year and a half while mortgage rates only caught up gradually.
  The ČNB itself notes that rate changes pass through to mortgages more slowly
  than to corporate loans, partly because existing mortgages are on fixed rates
  and only reprice at refixation.
- **Loan volumes move inversely to rates.** New mortgage volumes dropped as rates
  peaked in 2022–2023 and recovered as rates started falling.

## Note

The spread here is the gap between new-mortgage rates and the policy rate, used
as an indicator of how far mortgage pricing lags monetary policy — not a direct
measure of any single bank's profit.
