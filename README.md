# A/B Test — Revenue & Conversion Impact of Variant B

**Hypothesis (H1):** Variant B increases **conversion rate (CVR)** and **revenue per user (RPU)** vs. control.  
**OEC:** CVR (users with `revenue > 0` / users).  
**Secondary:** RPU; AOV among converters.  
**Alpha/Power:** 0.05 / 0.8, fixed-horizon (no peeking).  
**Guardrails:** N/A in this dataset.  
**Unit:** User-level randomization; one arm per user.

## Repo
```
ab-test-revenue/
│
├── data/               # analytic.csv, summary.csv, small plots (raw data excluded by default)
├── analysis/           # ab_analysis.ipynb (you'll add)
├── bi/                 # ab_summary.pbix (LFS), ab_summary.pdf (LFS)
├── docs/               # design.md, data_dictionary.md
└── .github/workflows/  # CI
```

## Run
1) Create a Python venv and `pip install -r requirements.txt`.  
2) Open `analysis/ab_analysis.ipynb`, set your CSV path, run all.  
3) Power BI → import `data/analytic.csv` & `data/summary.csv` → build one-pager → export to `bi/ab_summary.pdf`.

## Decision Rule
- **Ship** if 95% CI for CVR lift is entirely > 0 **and** abs lift ≥ +0.3pp  
- **Iterate** if CI straddles 0 or lift < +0.3pp  
- **No-ship** if negative or SRM failed (p < 0.01)

## Limitations
- No guardrails; CUPED skipped unless pre-period covariate exists.
