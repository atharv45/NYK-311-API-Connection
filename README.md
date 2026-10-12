# NYC 311 Complaints: API to Insights

**Goal:** Pull real data from a public API, clean it, remove duplicates (keep latest), and answer business questions with pandas.

**Data:** NYC 311 complaints (NYC Open Data API), [~50,000] rows, [Oct 4-9, 2026], nested JSON.

**Steps**
1. Pulled data page by page with `$limit` / `$offset`, saved raw JSON.
2. Flattened with `pd.json_normalize`.
3. Cleaned dates and text columns.
4. Deduplicated by `unique_key`, keeping the latest record (tested on simulated conflicting duplicates).
5. Created `days_to_close`; set [N] negative values to blank as data errors.

**Limitations:** Only 5 days of data. Open complaints are missing from time-to-close, so it's biased toward fast closures.

**Tools:** Python, pandas, requests, Google Colab
