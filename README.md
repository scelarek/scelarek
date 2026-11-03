<div align="center">

<img src="banner.svg" alt="Sam Celarek, Data Analyst with Nursing Background" width="100%"/>

<a href="https://scelarek.github.io/"><img src="https://img.shields.io/badge/Portfolio-FF8800?style=for-the-badge&logo=githubpages&logoColor=white" alt="Portfolio"/></a> <a href="https://www.linkedin.com/in/sam-celarek/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a> <a href="https://docs.google.com/document/d/1iOG1k-Rn-YsG7n76U7Kvuc9NowLHP8C4w8pklEHnjbc/edit?usp=sharing"><img src="https://img.shields.io/badge/Resume-2E7D32?style=for-the-badge&logo=googledocs&logoColor=white" alt="Resume"/></a> <a href="https://calendly.com/scelarek/60min"><img src="https://img.shields.io/badge/Book%20a%20call-555555?style=for-the-badge&logo=calendly&logoColor=white" alt="Book a call"/></a>

</div>

## Hi, I'm Sam

Data analyst with a nursing background, based in Portland, Oregon. I build end-to-end data tools with Python, SQL, APIs and AI, and I measure what they change.

- **3M+ IVF cycles** in the database I built as founding data analyst at [Baby Steps IVF](https://www.makebabysteps.com/), linking SART and CDC records and each clinic's pricing, insurance, doctors and services
- **30 → 1 minute** to prep each government RFP lead, with an 18-step Python and SQL pipeline I built at Nerevu Group
- **41% fewer** central line infections after a hospital quality improvement rollout I led as council chair

---

## What I've built

**[Baby Steps IVF](https://scelarek.github.io/pages/babysteps.html)** (2023 – present)
The data platform and models behind a site that lists 600 US fertility clinics and compares outcomes for nearly 400 of them across 3M+ IVF cycles.

- **Web data collection:** built a headless-browser scraper (Playwright, rotating proxies) for SART's clinic report filters, feeding a raw lake of about 960,000 report files. A constraint-lattice engine derives the filter combinations it never had to fetch, using inclusion-exclusion with zero tolerance for error, and re-scrapes of disputed cells matched its predictions exactly.
- **Database & ETL:** joined SART and CDC outcomes with each clinic's pricing, insurance, doctors, services and locations into a multi-table resource, including a 174M-row outcome-metrics table. A 50-step Python and SQL pipeline (Polars, DuckDB, PostgreSQL on Supabase) runs the weekly refresh. I'm migrating it from notebooks to tested scripts and piloting Dagster for orchestration.
- **Data quality:** linked clinic records across rebrands, mergers and duplicate registrations, with every match decision logged. The registry's own internal inconsistencies are flagged and kept per clinic-year instead of masked. Every refactor passes a byte-for-byte parity test against the previous output before it merges. pytest runs in GitHub Actions on every pull request, and Pandera schema checks are being added to each table write.
- **Price transparency:** built a database of 2,250+ clinic prices across 260+ clinics, each with its source page, quote and date, and an automated sweep re-confirmed 1,180 published prices against the live pages. Streamed multi-gigabyte insurer price-transparency files (UnitedHealthcare, Anthem, Cigna) and matched 2,682 provider NPIs, placing 624 of 700 clinics in at least one insurer network.
- **Analysis & modeling:** EDA across 28 years of registry data, then Bayesian hierarchical models (PyMC) of each stage from egg retrieval to live birth, adjusted for patient age and case mix and validated on held-out 2023–24 data. Release gates require convergence (r-hat at or below 1.025), 90% interval coverage and simulation-based calibration.
- **Causal analysis:** designed the causal framework for separating a clinic's own effect from the patients it treats, using a causal DAG, an instrumental-variable feasibility study and negative-control checks.
- **Model serving & deployment:** fitted the models with PyMC and serve them from Modal. Predictions and per-clinic-year timelines are precomputed in versioned bundles, checked against the previous build with a parity gate and published with a one-step rollback, so the site reads finished numbers with low latency. Separate staging and production targets, plus a code guard, keep unapproved model fits off the live site. The site runs on Vercel with preview deploys on every pull request, on a Supabase PostgreSQL backend whose migrations are tested on a fresh branch database before merge.
- **Automation & AI:** built a review hub with decision queues where data questions get resolved and recurring issues become automated rules. I run the work as a coordinated team of Claude Code agents (pipeline, modeling, cloud, data collection, backend, design) under a single merge queue, with independent code review and parity tests.

**[Nerevu Group](https://scelarek.github.io/pages/nerevu.html)** (2023 – 2026)
Sole programmer on our internal 18-step government RFP lead pipeline, which cut prep from about 30 minutes per lead to a 1-minute review. Before it, every lead was read and entered by hand, key dates were buried in long PDFs, and keyword search missed too many. The pipeline pulls leads from the HigherGov API and the web, extracts text from PDFs and XFA forms, uses OpenAI models to extract dates and fields and summarize each lead, then syncs everything to PostgreSQL and Airtable, with Zapier handling hand-offs. I chose models and settings on a validation set, scored them on a held-out test set, and cut cost with cached and parallel calls. It runs on Heroku with error logging and monitoring (New Relic, Prometheus, Papertrail). GitHub Actions CI runs 900+ tests plus an automated LLM code review, and every production error became a test that recreates it, pinned to the fix.

- **SQL Server and SSIS:** maintained nightly SQL Server and SSIS loads for a mortgage-lending client, with stored procedures, table-comparison reconciliation between staging and production, and SQL Server Agent email alerts.
- **Data governance:** produced the charts and executive recommendations table for a municipal data governance report.
- **Market disparity study:** designed the accuracy tests for the name-based classifiers that filled in missing demographic data, and produced charts and edits for the final report.
- **Hiring funnel and ATS:** customized our internal ATS and CRM dashboards, and analyzed a 1,000+ applicant funnel stage by stage to model which candidates advance.
- **Resume parsing:** built resume parsing for incoming applicants to feed the internal ATS.
- **LLM quality scoring:** wrote an automated scorer that grades LLM output inside the production pipeline.
- **Client websites:** updated a hospital's dashboard website, monitored with Prometheus, and made site updates for a university.

**[Nursing and quality improvement](https://scelarek.github.io/pages/quality.html)** (2014 – 2022)
Eight years as a nurse, five of them in neuro ICUs. Five years on a hospital Quality Improvement & Safety Council, rising from member to secretary, vice chair and chair. We used infection data, surveys and chart audits to find why line infections persisted, then led the fixes that cut them 41%.

---

## Tools

- **Data & SQL:** SQL Server / T-SQL, PostgreSQL, SSIS, DuckDB, SQLite, ETL pipelines, Pandera and Pydantic schemas, data validation and reconciliation
- **Analysis & modeling:** Python (pandas, Polars, scikit-learn), R, EDA, Bayesian hierarchical models (PyMC), causal inference, XGBoost, regression
- **Reporting:** Tableau, Power BI, Excel, dashboards and data visualization
- **Automation & AI:** REST APIs, LLM extraction and output scoring, Claude Code, GitHub Actions CI, pytest
- **Platforms:** Supabase, Vercel, Airtable, Heroku, Modal (model training and serving), FastAPI, AWS, Azure, New Relic, Prometheus, Papertrail
- **From BrainStation class work:** TensorFlow, Keras, PyTorch, NLTK, Spark, Hadoop, Hive, GCP, Docker, time series forecasting (Prophet, pmdarima, darts)

---

## Earlier projects (BrainStation Data Science, 2023)

- **[COVIDCast](https://scelarek.github.io/pages/covid.html):** epidemiological and machine learning time series models to forecast new COVID cases
- **[SideBard](https://scelarek.github.io/pages/sidebard.html):** a chatbot that uses embedded search to help users navigate AI features in Google Workspace
- [Kickstarter funding prediction](https://scelarek.github.io/pages/kickstart.html) · [West Nile virus modeling](https://scelarek.github.io/pages/wnv.html) · [Hotel review sentiment](https://scelarek.github.io/pages/hotel.html) · [Google Ngrams with AWS](https://scelarek.github.io/pages/google.html)
- [ML reference guides and templates](https://scelarek.github.io/pages/reference.html)

---

<div align="center">

**See more on my [portfolio](https://scelarek.github.io/)** · **[Email me](mailto:scelarek@gmail.com)** · **[Book a call](https://calendly.com/scelarek/60min)**

</div>
