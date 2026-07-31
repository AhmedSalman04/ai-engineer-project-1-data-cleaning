# Data Cleaning Decisions — Superstore Dataset

## Issue 1: Inconsistent date formats
**Finding:** `Order Date` and `Ship Date` contained three different date formats
mixed within the same columns (e.g., `11-08-2016`, `4/15/2017`, `06/12/2016`),
confirmed via pattern analysis (4,042 / 3,850 / 2,102 rows respectively for Order Date).

**Decision:** Parse all dates using pandas' mixed-format parser, standardize to
ISO 8601 format (YYYY-MM-DD) — the professional standard for date storage since
it's unambiguous and sorts correctly as plain text.

## Issue 2: Constant column (Country)
**Finding:** The `Country` column contained a single value ("United States") for
all 9,994 rows, confirmed via `.unique()`.

**Decision:** Dropped the column. It carries no analytical value since it never
varies, and country context is inferable from the `State` column if needed.

## Issue 3: Extreme negative profit values
**Finding:** The five largest losses (down to -$6,599.98) were investigated by
cross-referencing against the `Discount` column, revealing all were tied to
discounts of 70-80%.

**Decision:** No changes made. These are legitimate business outcomes (heavy
discounting causing losses), not data errors — removing them would hide a real
pattern rather than fix a mistake.