# Part Two: Design  
## Final Project — MIMIC-IV (Data Visualization)

This document defines visualization-driven questions, target audiences, analytic tasks, proposed design sketches, and the overall narrative for Part 2 of the Final Project.

---

# 1. Purpose of Part Two

The goal of this section is to clearly define **answerable** questions that can be addressed through visualization, identify the target audience, and outline tentative design sketches *before coding anything*. This ensures thoughtful planning before implementation.

---

# 2. Visualization Questions (3–5 Total)

Below are five visualization-oriented questions. Each includes:

- **Audience**
- **Task Type**
- **Data Elements**
- **Success Criteria**

---

## **Question 1 — How does hospital length of stay vary by admission type?**

**Audience:**  
Hospital quality teams, operational analysts, clinical managers.

**Task Type:**  
Comparison (distributions), trend-in-population.

**Data Elements:**  
- `admission_type`  
- Calculated `length_of_stay_hours`  

**Success Criteria:**  
A viewer should be able to quickly see which admission types (Emergency, Elective, Urgent) have the longest stays and how wide the variability is.

---

## **Question 2 — What are the most frequent diagnoses (ICD codes) observed in the hospital population?**

**Audience:**  
Clinical researchers, epidemiologists, health policy analysts.

**Task Type:**  
Ranking, categorical frequency analysis.

**Data Elements:**  
- `diagnoses_icd.icd_code`  
- Count of admissions associated with each code  

**Success Criteria:**  
The top diagnoses must be immediately identifiable and interpretable from the visualization.

---

## **Question 3 — What procedures often occur together for the same patients or same admissions?**

**Audience:**  
Clinical administrators, surgery department coordinators.

**Task Type:**  
Association / co-occurrence detection.

**Data Elements:**  
- `procedures_icd.icd_code`  
- Frequency of codes co-occurring within the same `hadm_id`  

**Success Criteria:**  
Clear identification of clusters or frequently paired procedures.

---

## **Question 4 — Which microbiology organisms are most common, and how does distribution change over time?**

**Audience:**  
Hospital infection control teams, microbiology staff.

**Task Type:**  
Distribution + temporal pattern detection.

**Data Elements:**  
- `microbiologyevents.organism`  
- `charttime` (if available)  

**Success Criteria:**  
Ability to easily identify the dominant organisms and detect any seasonal or temporal surges.

---

## **Question 5 — What hospital services handle the majority of admissions?**

**Audience:**  
Hospital administrators, service line managers.

**Task Type:**  
Ranking and high-level comparison.

**Data Elements:**  
- `services.curr_service`  
- Count of services per admission  

**Success Criteria:**  
The top services should be visually distinct and easy to interpret for capacity planning.

---

# 3. Hand-Sketch Prototypes (4–6 Sketches)

Below are *Markdown descriptions* of sketches.  
A separate PDF with hand-drawn sketches will accompany the final submission.

---

## **Sketch 1 — Boxplot: Length of Stay by Admission Type**

**Marks:**  
- Points for individual LOS values (optional)  
- Boxplot rectangles  

**Channels:**  
- Position (y): length of stay (hours)  
- Position (x): admission_type categories  
- Outlier markers for extreme stays  

**Annotations:**  
- Clear axis labels  
- Units: hours  
- Optional interaction: tooltips for summary stats  

---

## **Sketch 2 — Bar Chart: Top 15 Diagnoses (ICD Codes)**

**Marks:**  
- Horizontal bars  

**Channels:**  
- Length: count of ICD occurrences  
- Position (y): ICD codes  

**Annotations:**  
- Label bars with counts  
- Include a legend for ICD description (if merged later)  

---

## **Sketch 3 — Network Diagram: Procedures Co-Occurrence**

**Marks:**  
- Nodes (procedures)  
- Links (co-occurrence strength)  

**Channels:**  
- Node size: frequency of procedure  
- Link thickness: co-occurrence count  
- Color hue: procedure category (if applicable)

**Annotations:**  
- Tooltip or click interaction to highlight a node’s neighbors  

---

## **Sketch 4 — Time Series + Bar Distribution: Microbiology Organisms**

**Marks:**  
- Line chart (time dimension)  
- Bar chart for top organisms  

**Channels:**  
- Position x: calendar time  
- Position y: count of events  
- Color hue: organism type  

**Annotations:**  
- Axis labels for time and event counts  
- Legend mapping organism → color  

---

## **Sketch 5 — Bar Chart: Service Utilization Counts**

**Marks:**  
- Vertical bars  

**Channels:**  
- Height: number of admissions per service  
- Color saturation: relative volume  

**Annotations:**  
- Rotated x-labels if service names are long  

---

## **Sketch 6 — Optional Dashboard Layout (Storyboard)**

**Scene 1:** High-level overview — service volume, top diagnoses.  
**Scene 2:** Drill-down — length of stay patterns.  
**Scene 3:** Microbiology & infection trends.  
**Scene 4:** Procedure interactions or networks.

The viewer moves from **broad hospital patterns → detailed clinical clusters**.

---

# 4. Storyboard (Optional)

A proposed multi-view dashboard flow:

1. **Start with system-wide metrics**  
   - Service distribution  
   - Top diagnoses  

2. **Move into stay characteristics**  
   - Length of stay by admission type  
   - Distribution spread + outliers  

3. **Zoom into clinical details**  
   - Most common organisms  
   - Temporal patterns  

4. **Relationship-level views**  
   - Procedure co-occurrence  

This flow allows the user to progress from *population-level understanding* to *clinical insights*.

---

# 5. Deliverables for Part 2

This submission includes:

- `report_part2.md` (this file)  
- A single combined PDF file with all hand-drawn sketches and annotations  

---

# 6. Checklist

- [x] Audience explicitly defined  
- [x] Tasks categorized clearly  
- [x] Each visualization question has success criteria  
- [x] Sketches include marks, channels, and annotations  
- [x] Optional storyboard provided  

---

# End of Part Two