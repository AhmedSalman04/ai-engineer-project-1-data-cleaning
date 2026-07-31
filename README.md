# Superstore Sales Data Cleaning Pipeline

## Overview
This project cleans and validates a retail sales dataset (9,994 orders) to
prepare it for reliable reporting and analysis — the kind of internal data
quality work that underpins accurate business dashboards and decision-making.

## Issues Found & Fixed
See [decisions.md](decisions.md) for full reasoning behind each decision.

1. **Inconsistent date formats** — Order Date and Ship Date contained three
   different formats mixed within the same columns. Standardized to ISO 8601.
2. **Uninformative constant column** — Country contained a single value across
   all rows and was removed as analytically redundant.
3. **Investigated extreme profit outliers** — confirmed as legitimate results
   of steep discounting rather than data errors; left unchanged and documented.

## Validation
- Row count preserved: 9,994 rows before and after cleaning
- No logically impossible records (e.g., ship date before order date)
- All date fields now machine-readable and sortable

## Files
- `superstore_raw.csv` — original dataset
- `superstore_cleaned.csv` — cleaned output
- `data_exploration.ipynb` — full process, from diagnosis through validation
- `decisions.md` — reasoning log for each cleaning decision

## Tools
Python, pandas