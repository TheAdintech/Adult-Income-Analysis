# Adult-Income-Analysis

### Adult-Income-Analysis — PostgreSQL & Python

This is an exploratory analysis of income patterns using SQL and Python. I built this project as a testament to my learning journey with PostgreSQL — coming from a background in MSSQL — and to prove I could handle the full pipeline from raw data to analysis using pandas.

## Overview

This project explores what factors correlate with income level in a historical workers dataset — age, education, occupation, hours worked, marital status, and more. The goal wasn't just to run queries, but to practice the full analyst workflow: clean data, ask real questions in SQL, then bring results into Python for deeper analysis and visualization.

## Dataset

Source: Adult Census Income dataset (1994 US Census data), ~43,957 rows.

Columns include age, education, occupation, marital status, race, gender, hours worked per week, capital gains/losses, native country, and a binary income flag (`income_>50K`).

**Important caveats:**
- `income_>50K` is a binary flag (0/1), not a continuous income figure
- Data reflects the US economy in 1994 — patterns may not hold today
- `educational_num` is an ordinal rank (1–16), not literal years of schooling

## Pipeline
Raw CSV (workers_data.csv)

│

▼

PostgreSQL (create_table.sql → import_data.sql)

│

▼

SQL Analysis (analysis_queries.sql)

│

▼

SQLAlchemy Connection (.env → engine)

│

▼

Pandas DataFrames (pd.read_sql)

│

▼

Visualization & Profiling (Matplotlib, ydata-profiling)

## Tools & Stack
- PostgreSQL
- SQLAlchemy
- Python (pandas, matplotlib, numpy)
- ydata-profiling
- Jupyter Notebook

## Repo Structure
workers-data-postgres-analysis/
├── README.md
├── .gitignore
├── postgreSQL/
│ ├── create_table.sql
│ ├── import_data.sql
│ └── analysis_queries.sql
├── notebooks/
│ └── analysis.ipynb
├── scripts/
│ └── visualize.py
├── reports/
│ └── profile_report.html
├── data/
│ └── workers_data.csv
└── requirements.txt

## Key Findings

- **Age gap by income bracket**: Workers earning above $50K average ~44 years old, vs ~37 for those earning below — suggesting income tracks career experience more than age alone.
- **Education shows diminishing returns**: HS-grad → Bachelors raises the >50K earning rate by ~26 percentage points, but Bachelors → Masters only adds ~14pp.
- **Non-US earners**: Among non-US-born workers, India has the highest proportion earning above $50K (42%, n=134), followed by France (41%, n=32) and Taiwan (38%, n=58) — these sample sizes were checked to rule out small-sample distortion.
- **Weak correlations**: Education and hours worked show only a weak positive correlation with capital gains — education alone doesn't strongly predict investment income in this dataset.

## Caveats & Limitations

- Correlation does not imply causation — relationships found here are descriptive, not causal
- 1994 data does not reflect the modern economy, job market, or cost of living
- The binary income flag limits granularity — we can't see *how much* above $50K someone earns

## How to Reproduce

1. Clone this repository
2. Install PostgreSQL locally
3. Create a `.env` file in the repo root with your own database credentials (see below)
4. Run `create_table.sql` and `import_data.sql` to set up the database
5. Install Python dependencies: `pip install -r requirements.txt`
6. Open `notebooks/analysis.ipynb` and run all cells

## **.env format:**
- DB_USER=your_username
- DB_PASSWORD=your_password
- DB_HOST=localhost
- DB_PORT=5432
- DB_NAME=your_database_name

## Author
Isaac Adinoyi Joseph<br>
Pure Mathematics Student, Data Analyst and Scientist
