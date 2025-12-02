# Part Three — Implementation I (Submission)

## Contents
- `viz/` — produced visuals (HTML, PNG)
- `code/` — scripts used to build the visuals
- `report_part3.md` — report with mapping tables and accessibility details
- `requirements.txt` — Python packages
- `environment.yml` — conda environment (optional)

## How to view
- Open `viz/viz1_diagnosis_network.html` in a browser to interact with the network.
- Open `viz/*.png` with any image viewer.

## How to re-generate
1. Create python environment:
python -m venv venv
source venv/bin/activate # or venv\Scripts\activate on Windows
pip install -r requirements.txt

2. Run scripts:
python code/viz_matplotlib.py
python code/viz_plotly.py
python code/viz_bokeh.py

The scripts will write images/HTML into `viz/`.

## Notes
- Network and interactive HTMLs are client-side and do not require a server.
- For large datasets, the `top_n` parameter in the code controls graph size.
