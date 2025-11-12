# Instructions for Reproducibility  
## Final Project — MIMIC-IV (Data Visualization)

This document provides a complete, reproducible workflow for **Part 1: Data & Exploration** of the final project.  
It explains the project layout, installation steps, dataset placement, and instructions for running the EDA notebook.  
As future project components are added, this file will be updated accordingly.

# 1. Project Structure

Your project directory should follow this layout:

Final-Project/
│
├── admissions.csv
├── diagnoses_icd.csv
├── procedures_icd.csv
├── microbiologyevents.csv
├── services.csv
│
├── notebooks/
│ └── DV-Final-Project-Part1.ipynb
│
├── figures/
│ └── part1/
│
├── report_part1.md
├── instructions.md
├── requirements.txt
└── environment.yml

The folder `figures/part1/` will be created automatically when you run the notebook.

# 2. Software Requirements

### Python Environment
A working Python installation (version **3.9 or newer**) is required.  
Using **Anaconda** or **Miniconda** is strongly recommended.

### Required Python Packages
The project depends on:

- pandas  
- numpy  
- matplotlib  
- seaborn  
- jupyterlab or notebook  

### Installing Dependencies

Using `requirements.txt`:

pip install -r requirements.txt

Using Conda:

conda env create -f environment.yml
conda activate dv-final

# 3. Dataset Preparation

Place the following files directly inside your main project folder:

admissions.csv
diagnoses_icd.csv
procedures_icd.csv
microbiologyevents.csv
services.csv

Your dataset should be located in:

C:\Users\muham\OneDrive\Desktop\Desktop 11032025\PhD Computer Science\DV\Final-Project\

No subfolders are needed for the raw CSV files.

# 4. Running the EDA Notebook

### Step 1 — Start Jupyter

jupyter notebook

### Step 2 — Open the EDA Notebook

Navigate to:

notebooks/DV-Final-Project-Part1.ipynb

### What the Notebook Does

The notebook will automatically:

- Load all five CSV tables  
- Inspect table schemas and data types  
- Compute missingness statistics  
- Generate numeric and categorical summaries  
- Produce distribution visualizations  
- Compute ICD frequency counts  
- Analyze service types and microbiology organisms  
- Validate shared keys (e.g., `hadm_id`)  
- Save every generated figure into:

figures/part1/

All plots, tables, and diagnostics for **Part 1** come from running this notebook.

# 5. Figure Output

All visualizations created during EDA are exported to:

figures/part1/

If you need to clear previously generated figures:

### Windows:
del figures\part1*.png

### Mac/Linux:
rm figures/part1/*.png

# 6. Reproducibility Checklist (Part 1)

Before submitting Part 1, verify the following:

### Required Files
- `report_part1.md`  
- `instructions.md`  
- `requirements.txt` or `environment.yml`  
- `notebooks/DV-Final-Project-Part1.ipynb`  
- Figures stored under `figures/part1/`  

### Code Quality Requirements
- Notebook executes from start to finish without errors  
- All paths are configurable and not hard-coded incorrectly  
- Figures export correctly  
- Summary tables and missingness checks appear as expected  

### Documentation Requirements
- Data pitch included in `report_part1.md`  
- Ethical considerations and provenance documented  
- Data readiness plan explained clearly  
- Relationship between tables (admissions → diagnoses → procedures → microbiology → services) documented  

# 7. Data Source, Provenance & Ethics

These files originate from a processed extract of **MIMIC-IV**, maintained by PhysioNet.  
Use of this dataset comes with ethical responsibilities:

### Ethical Guidelines
- Never attempt patient re-identification  
- Understand that dates are shifted to protect privacy  
- Ages 89+ may be grouped into a single category  
- Limit all use to academic or non-commercial work  
- Follow all HIPAA-compliant handling guidelines  

Document full provenance in your `report_part1.md`.

# 8. Notes for Future Project Parts

As you progress, this file will expand.  
Future sections will include:

- Part 2 → Data Cleaning Workflow  
- Part 3 → Feature Engineering Steps  
- Part 4 → Visualization Design Choices  
- Part 5 → Dashboard / Interactive Components  
- Part 6 → Narrative Construction & Analytical Storytelling  
- Part 7 → Final Packaging & Deliverables  

# 9. Troubleshooting

### CSV File Not Found
Confirm file names match exactly:

admissions.csv
diagnoses_icd.csv
procedures_icd.csv
microbiologyevents.csv
services.csv

### Plots Not Appearing
Restart the notebook kernel and re-run all cells.

### Path Errors
Ensure that the `BASE_DIR` variable inside the notebook matches:

C:\Users\muham\OneDrive\Desktop\Desktop 11032025\PhD Computer Science\DV\Final-Project\

# 10. Contact

For questions about the project structure or reproducibility process, refer to the course instructions or contact your instructor.

# ✅ End of Instructions (Part 1)
