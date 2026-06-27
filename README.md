# Financial Ratio Engine — Sprint 2

## Structure
```
ratio_engine/
├── src/
│   ├── analytics/
│   │   ├── ratios.py          # Profitability, leverage, efficiency ratios
│   │   ├── cagr.py            # CAGR engine (3/5/10-yr, 6 edge cases)
│   │   └── cashflow_kpis.py   # CFO quality, CapEx intensity, FCF, capital allocation
│   └── db/
│       ├── schema.py          # SQLite schema & migrations
│       └── loader.py          # Data ingestion from companies.xlsx
├── tests/kpi/                 # 20 KPI formula unit tests
├── output/                    # capital_allocation.csv, ratio_edge_cases.log
├── data/                      # companies.xlsx (place here)
├── run_engine.py              # Full pipeline runner
└── requirements.txt
```

## Setup
```bash
pip install -r requirements.txt
python run_engine.py           # Populates financial_ratios table
python -m pytest tests/ -v     # Runs all 20 unit tests
```

## Exit Criteria
- `SELECT COUNT(*) FROM financial_ratios` → ≥ 1,100 rows
- All 14 KPI columns populated — zero null-only columns
- All 20 KPI formula unit tests pass (0 failures)
- Manual spot-check: ROE and Revenue CAGR for 3 companies within 0.1%
- `output/ratio_edge_cases.log` — every anomaly explained
