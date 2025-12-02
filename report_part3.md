# Part Three — Implementation I

**Author:** Muhammad Zaheer Sajid  
**Date:** 12/01/2025

---

## 1. Overview

This submission contains three implemented visuals that operationalize the proposed design for examining hospital admissions and diagnosis relationships. Visuals include an interactive diagnosis co-occurrence network, a small-multiples temporal view of weekly admissions for top ICDs, and a granularity-change network that collapses detail into aggregated groups.

Files:
- `viz/viz1_diagnosis_network.html` — interactive network (detail + aggregated toggle)
- `viz/viz2_weekly_icd_smallmultiples.png` — small multiples (weekly admissions per top ICD)
- `viz/viz3_diagnosis_network.html` — network demonstrating granularity change (or use `viz1_diagnosis_network.html` which contains both)
- `viz/viz3_data.json` — data used by the interactive HTML
- `code/` — scripts used to build visuals
- `report_part3.md` — this file

---

## 2. How to view/run

1. Unzip the submission folder.
2. Open `viz/viz1_diagnosis_network.html` in a modern browser (Chrome/Firefox). No server required.
3. Open PNG files in any image viewer.
4. To re-generate visuals: see `code/` for scripts and run `python viz_bokeh.py` / `python viz_plotly.py` / `python viz_matplotlib.py`.

---

## 3. Cognitive mapping tables

### Viz 1 — Interactive Network
| Visual element | Data encoded | Channel | Task |
|---|---:|---|---|
| Node position | ICD co-occurrence clusters | position (x,y) | identify community/clusters |
| Node size | degree (number of connections) | area | detect prominence |
| Edge width | co-occurrence count | width | compare relation strength |
| Color | ICD group / first-letter | color | categorize groups |
| Tooltip | ICD id + counts | text | retrieve exact values |

### Viz 2 — Small Multiples (Temporal)
| Visual element | Data encoded | Channel | Task |
|---|---:|---|---|
| X axis | week (time) | position (x) | read trends |
| Y axis | admission counts | position (y) | compare magnitude |
| Facet position | ICD code | spatial grouping | compare shapes across ICDs |
| Line color | same across facets | color | consistent visual decoding |

### Viz 3 — Granularity Change (Aggregated <-> Detail)
| Visual element | Data encoded | Channel | Task |
|---|---:|---|---|
| Node grouping | diagnosis vs group | spatial grouping | move between summary/detail |
| Dropdown/interaction | toggle view | interaction | change granularity |
| Node size & color | prominence / group | area & color | highlight important nodes |

---

## 4. Accessibility & quality gates

- **Palette:** Okabe–Ito / Tableau10 (color-blind safe). Example hex set used: `#E69F00`, `#56B4E9`, `#009E73`, `#F0E442`, `#0072B2`, `#D55E00`, `#CC79A7`, `#000000`.
- **Text size:** All web UI labels and legends use >= **12 pt** (≈16px). PNGs generated with readable fonts; plot labels use `fontsize=12–14`.
- **Contrast:** Ensure WCAG AA contrast for text vs background. Use white or near-white node labels on dark nodes, dark text on light backgrounds.
- **Alt text:** Provide alt text for each image (examples below).
- **Keyboard & responsive layout (web):** HTML interactive supports focusable controls for switching views (dropdown) and zoom/pan with mouse. To improve keyboard access, tab-index the dropdown and provide keyboard handlers for view change.
- **Avoid chartjunk:** No unnecessary 3D effects, shadows, or decorative elements.

**Alt text examples**
- Viz1: “Interactive diagnosis co-occurrence network showing ICD nodes and edges; node size indicates degree and edge width indicates frequency of co-occurrence.”
- Viz2: “Small multiples showing weekly admission counts for the top ICD diagnosis codes; each panel is a time series for one ICD.”
- Viz3: “Aggregated network view showing diagnosis groups and a toggle to view detailed diagnosis-level network.”

---

## 5. Reproducible environment

See `requirements.txt` (Python packages) or `environment.yml` for conda reproducibility.

---

## 6. Notes & limitations

- Network uses top-N ICDs to keep interaction fast. This choice and parameter (top_n) are noted in code.
- Future improvements: keyboard navigation, ARIA attributes in HTML, server-hosted variant for remote access.

---

## 7. Summary

This submission contains three distinct visuals fulfilling the assignment constraints: one interactive, one small-multiples/temporal, one granularity-change non-cartesian visualization. Cognitive mapping and accessibility considerations are included.

