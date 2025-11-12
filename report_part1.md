# Part One: Data & Exploration — MIMIC-IV

## Submission Format
- A GitHub repo with code + data pointers (Repo Provided).  
- This summary file (`report_part1.md`) describing what you did and why.  
- Exported figures as PNG/SVG/HTML as appropriate.  
- Reproducibility file (`requirements.txt`/`environment.yml`).  
- Reproducibility instructions (`instructions.md`) updated for all phases.

# Goal
Choose an authentic dataset and demonstrate understanding of its **structure**, **quirks**, and **analytical potential**.

# Dataset: MIMIC-IV (Medical Information Mart for Intensive Care)

**Source:** https://physionet.org/content/mimiciv/  
**License:** PhysioNet Credentialed Health Data License 1.5.0  
**Access:** Requires CITI training and PhysioNet approval  
**Version:** 2.2 (or latest)  
**Scale:** Millions of rows, 20+ relational tables  
**Structure:** Temporal, hierarchical  
**Time Span:** 2008–2019  

### Dataset Sufficiency (meets all criteria)
- ≥ 50k rows (MIMIC-IV has **hundreds of millions**)  
- Multi-table **relational** dataset  
- **Temporal + hierarchical** structure  
- **High complexity** with multiple event types and entities  

# 1. Data Pitch

## Problem / Context
ICUs generate dense, high-frequency data across labs, vitals, medications, procedures, and clinical notes.  
These signals contain crucial information on:

- Patient deterioration  
- Treatment pathways  
- Comorbidity burden  
- Resource utilization  
- Outcomes and risk profiles  

Challenges include irregular sampling, missingness, and massive scale.  
MIMIC-IV provides a real, de-identified dataset enabling transparent, reproducible ICU analysis.

## Audience
- Clinical researchers  
- ICU/healthcare data scientists  
- Hospital operations teams  
- Students learning medical data analytics  

## Source, License, Access, Cadence
- **Source:** PhysioNet (MIT & BIDMC)  
- **License:** PhysioNet Credentialed Health Data License  
- **Access:** Requires CITI certification  
- **Refresh cadence:** ~every 1–2 years  

## Risks (Bias, Missingness, Privacy, Representativeness)

### Privacy
- Patient identifiers removed  
- All timestamps shifted  
- Ages >89 bucketed  
- Small residual re-identification risk remains  

### Missingness
- Clinical measurements taken only when needed  
- Vitals sampled irregularly  
- Medications sometimes missing timestamps  
- Data is **not missing at random** (MNAR)

### Representativeness
- Single-center academic hospital  
- Not generalizable to global populations  

### Workflow Bias
- Measurement frequency correlates with severity  
- Timestamp quirks due to EHR updates  

**Mitigation:** document limitations clearly, avoid causal claims, use data only for research/education.

# 2. EDA Summary  
*(Full analysis in `notebooks/eda_part1.ipynb`.)*

## Schema & Data Dictionary
MIMIC-IV consists of three modules:

### Core  
- `patients`  
- `admissions`  
- `transfers`

### Hosp  
- `labevents`  
- `diagnoses_icd`  
- `procedures_icd`  
- `prescriptions`  
- `microbiologyevents`

### ICU  
- `icustays`  
- `chartevents`  
- `inputevents`  
- `outputevents`  
- `datetimeevents`


## Summary Stats

### Patients
- Age distribution: 50–85 is common (HIPAA >89 = 89+)  
- Sex fairly balanced  
- Mortality rates 8–12% in ICU cohorts  

### Admissions
- Median LOS ≈ 5 days  
- Mostly emergency admissions  
- Many patients with multiple hospital visits  

### ICU Stays
- Median ICU LOS ≈ 2 days  
- ~250k ICU stays  

## Distributions, Missingness & Outliers

### Distributions
- Vitals: multimodal, high variance  
- Labs: skewed with long tails  
- Length of stay: heavy-tailed  

### Missingness
- Driven by clinical decision-making  
- Entire vital sign blocks missing at times  
- Lab frequency varies by condition severity  
- Missing timestamps in medication data  

### Outliers
- Unit inconsistencies in some lab items  
- Duplicate chart events  
- EHR maintenance windows cause timestamp drift  

## Early Hypotheses
1. First-24-hour vital sign abnormalities predict mortality.  
2. Lab trajectories (e.g., lactate, creatinine) cluster by severity.  
3. Medications administered early may indicate risk category.  
4. ICU service unit (MICU/SICU/CCU) affects measurement patterns.  

# 3. Data Readiness Plan

## Cleaning
- Standardize all time fields  
- Normalize lab measurement units  
- Remove duplicates (especially in `chartevents`)  
- Filter `itemid` lists for meaningful variables  
- Identify and cap physiologically impossible values  

## Joining Strategy

To combine patient, admission, ICU, and event-level data, the project uses the following relational structure:

patients
    ↓
admissions
    ↓
icustays → labevents / chartevents / prescriptions / diagnoses

## Derived Features

### Patient-Level Features
- Age, sex  
- Comorbidity indices (Charlson or Elixhauser)  
- Previous admissions  

### Stay-Level Features
- ICU LOS  
- Hospital LOS  
- First-24-hour vitals & labs (min, max, median, slopes)  
- Count of early abnormalities  

### Event-Level Features
- Hourly vital sign summaries  
- Lab trajectories  
- Medication frequencies  

## Constraints

### Time Constraints
- Limit analysis to the **first ICU stay per patient**  
- Focus on **first 24 hours** for early signal identification  

### Computational Constraints
- `chartevents` ≈ 400M rows → **cannot load entirely**  
- Strategy:
  - DuckDB / SQL  
  - Columnar storage (Parquet)  
  - Targeted filtering  

## Feasibility
- Dataset size manageable with proper tooling  
- Aggregated views allow effective EDA  
- Derived features enable downstream modeling  

## Deliverables
- `report_part1.md` (this file)  
- `notebooks/eda_part1.ipynb`  
- `data_dictionary.md`  
- Exported figures (PNG/SVG/HTML)  
- Reproducibility files (`requirements.txt`, `environment.yml`)  
- Updated `instructions.md`  

## Checklist
- [x] Dataset meets ≥2 sufficiency criteria  
- [x] License & provenance documented  
- [x] EDA includes distributions, missingness, and signal exploration  
- [x] Risks & ethics addressed  

