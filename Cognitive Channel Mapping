# Cognitive Channel Mapping

## Visualization 1 – Interactive Diagnosis Explorer (Plotly)

| Channel / Cue        | How you used it (specifics)                                   | Why it helps cognition / reduces error                     |
|----------------------|----------------------------------------------------------------|--------------------------------------------------------------|
| **Position**         | X-axis = Diagnosis category (ICD); Y-axis = frequency counts   | Most accurate way to compare quantitative values            |
| **Length**           | Bar height represents diagnosis frequency                      | Makes category comparison fast and intuitive                |
| **Angle/Slope**      | Not used                                                       | Reduces unnecessary complexity                              |
| **Area/Size**        | No area encoding; tooltips show exact numbers                  | Prevents area-based misinterpretation                       |
| **Density/Texture**  | Not used                                                       | Keeps the interface clean and readable                      |
| **Color saturation** | Used to distinguish filtered vs non-filtered states            | Supports quick, pre-attentive identification                |
| **Color hue**        | Different hues for admission types (ED, elective, urgent)      | Helps users distinguish groups; color-blind-safe palette    |
| **Shape**            | Not used                                                       | Avoids over-encoding and clutter                            |
| **Containment**      | Filters grouped in dropdown panels                             | Makes interaction options visually organized                |
| **Annotations/Labels** | Hover labels provide ICD description + count                | Reduces legend chasing; supports accessibility              |

---

## Visualization 2 – Small-Multiples Temporal Admissions Trend

| Channel / Cue        | How you used it (specifics)                                   | Why it helps cognition / reduces error                      |
|----------------------|----------------------------------------------------------------|---------------------------------------------------------------|
| **Position**         | X-axis = time; Y-axis = admission counts                       | Clarifies weekly trends and temporal comparisons              |
| **Length**           | Height of line segments encodes magnitude                      | Enables accurate reading of differences across panels         |
| **Angle/Slope**      | Slope shows acceleration/decline in admissions                 | Highlights sudden spikes or dips                             |
| **Area/Size**        | Not used                                                       | Avoids misleading visual mass                                |
| **Density/Texture**  | Not used                                                       | Maintains a clean layout                                     |
| **Color saturation** | Uniform saturation across panels                               | Avoids unintentional ranking cues                            |
| **Color hue**        | Separate hues for different service categories                 | Clear differentiation while staying color-blind-safe          |
| **Shape**            | Optional point markers on lines                                | Improves accuracy at individual timepoints                   |
| **Containment**      | Grid of small multiples (one per service)                      | Allows safe comparison without overplotting                  |
| **Annotations/Labels** | Titles, axis labels ≥12pt; peaks labeled                    | Boosts accessibility and reduces cognitive load              |

---

## Visualization 3 – Non-Cartesian Service Interaction Network

| Channel / Cue        | How you used it (specifics)                                   | Why it helps cognition / reduces error                      |
|----------------------|----------------------------------------------------------------|---------------------------------------------------------------|
| **Position**         | Force-directed layout brings related services closer           | Naturally visualizes clusters and strong relationships        |
| **Length**           | Not applicable                                                 | Removes irrelevant encodings                                 |
| **Angle/Slope**      | Not used                                                       | Prevents confusion in a nonlinear layout                      |
| **Area/Size**        | Node size = patient volume / interaction strength              | Helps users detect important nodes instantly                  |
| **Density/Texture**  | Edge density maps to interaction frequency                     | Highlights service clusters pre-attentively                  |
| **Color saturation** | Higher saturation for higher-importance nodes                  | Supports quick magnitude estimation                           |
| **Color hue**        | Different hues for service types (clinical vs surgical etc.)   | Clear categorical separation with color-blind-safe palette    |
| **Shape**            | Different shapes for service nodes vs patient categories       | Redundant cue enhances accessibility                          |
| **Containment**      | Clusters form natural boundaries around service families       | Makes grouping intuitive for viewers                          |
| **Annotations/Labels** | Node labels + hover tooltips show service name + count     | Eliminates ambiguity and supports interpretability            |

---
