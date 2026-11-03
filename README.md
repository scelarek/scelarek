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

- **Database & ETL:** joined SART and CDC outcomes with each clinic's pricing, insurance, doctors, services and locations into a multi-table resource, including a 174M-row outcome-metrics table. A 50-step Python and SQL pipeline (Polars, DuckDB, PostgreSQL on Supabase) runs the weekly refresh.
- **Data quality:** linked clinic records across rebrands, mergers and duplicate registrations, with every match decision logged. The registry's own internal inconsistencies are flagged and kept per clinic-year instead of masked. Derived values are checked against source data with zero tolerance for error.
- **Price transparency:** built a database of 2,250+ published clinic prices across 260+ clinics, each tied to its public source and date and re-verified. Processed the insurers' public multi-gigabyte price-transparency files (UnitedHealthcare, Anthem, Cigna) and matched 2,682 provider NPIs, placing 624 of 700 clinics in at least one insurer network.
- **Testing & CI:** pytest runs in GitHub Actions on every pull request, and every refactor must pass a byte-for-byte parity test against the previous output before it merges. All changes go through a single merge queue with independent code review. Database migrations are tested on a fresh Supabase branch database, and every pull request gets a Vercel preview deploy.
- **Analysis & modeling:** EDA across 28 years of registry data, then Bayesian hierarchical models (PyMC) of each stage from egg retrieval to live birth, adjusted for patient age and case mix and validated on held-out 2023–24 data. Release gates require convergence (r-hat at or below 1.025), 90% interval coverage and simulation-based calibration.
- **Causal analysis:** designed the causal framework for separating a clinic's own effect from the patients it treats, using a causal DAG, an instrumental-variable feasibility study and negative-control checks.
- **Model serving & deployment:** fitted the models with PyMC and serve them from Modal. Predictions and per-clinic-year timelines are precomputed in versioned bundles, checked against the previous build with a parity gate and published with a one-step rollback, so the site reads finished numbers with low latency. Separate staging and production targets, plus a code guard, keep unapproved model fits off the live site. The site runs on Vercel on a Supabase PostgreSQL backend.
- **Automation & AI:** built a review hub with decision queues where data questions get resolved and recurring issues become automated rules. I run the work as a coordinated team of Claude Code agents (pipeline, modeling, cloud, backend, design).

**[Nerevu Group](https://scelarek.github.io/pages/nerevu.html)** (2023 – 2026)
Built and maintained our internal government RFP lead pipeline (about 98% of the code commits), which cut prep from about 30 minutes per lead to a 1-minute review. Before it, every lead was read and entered by hand, key dates were buried in long PDFs, and keyword search missed too many. A 17-stage Python pipeline on Heroku pulls opportunities from HigherGov (API, CSV exports and opportunity pages), finds new and changed leads, and fetches their documents. It extracts text from PDFs (PyMuPDF with Tesseract OCR, and XFA forms flattened with Aspose), Word files and spreadsheets, and removes duplicate documents by content hash. OpenAI's o4-mini summarizes each document and extracts and classifies about 40 fields per lead, including dates, contacts, budget, set-aside and pre-bid conferences, under a strict no-fabrication prompt. Results land in Airtable, where the team works, with locked columns so the pipeline never overwrites human edits, and PostgreSQL holds the tables between stages. LLM calls run asynchronously with concurrency limits, retries and per-run cost tracking. The pipeline is monitored with New Relic, emails a status report after each run, and is covered by 611 pytest tests.

- **SQL Server and SSIS:** maintained nightly SQL Server and SSIS loads for a mortgage-lending client, with stored procedures, table-comparison reconciliation between staging and production, and SQL Server Agent email alerts.
- **Data governance:** produced the charts and executive recommendations table for a municipal data governance report.
- **Market disparity study:** designed the accuracy tests for the name-based classifiers that filled in missing demographic data, and produced charts and edits for the final report.
- **Hiring funnel and ATS:** analyzed our recruiting pipeline, starting with 600+ applicants for one data analyst opening. I cleaned the ATS data, tracked time to hire, stage advancement and withdrawals by job board, tested whether candidate quality differed by source with logistic regression and imbalanced classification, and recommended stricter early screening to cut manual review. I also customized our internal ATS and CRM dashboards.
- **Resume parsing:** extended CVInsight, an open-source LLM resume parser, with custom plugins that extract education, work experience, job-relevant experience and social profiles, plus tests and documentation, then ran it on our applicant resumes.
- **LLM quality scoring:** wrote an automated scorer that grades LLM output inside the production pipeline.
- **Client websites:** updated a hospital's dashboard website, monitored with Prometheus, and made site updates for a university.

**[Nursing and quality improvement](https://scelarek.github.io/pages/quality.html)** (2014 – 2022)
Eight years as a nurse, five of them in neuro ICUs. Five years on a hospital Quality Improvement & Safety Council, rising from member to secretary, vice chair and chair. We used infection data, surveys and chart audits to find why line infections persisted, then led the fixes that cut them 41%.

---

## Tools

- **Data & SQL:** SQL Server / T-SQL, PostgreSQL, SSIS, DuckDB, SQLite, ETL pipelines, Pydantic schemas, data validation and reconciliation
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
