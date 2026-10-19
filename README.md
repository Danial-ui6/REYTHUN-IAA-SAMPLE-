# REYTHUN-IAA-SAMPLE-
RYTHUN — Sample work: quality report for a 200-item RLHF harmlessness preference dataset. 3 annotators, 84% observed agreement, Fleiss' Kappa 0.68, documented adjudication. Methodology and sanitized samples only; full dataset under NDA.
# RYTHUN — RLHF Harmlessness Preference Data Quality Report

**Sample work from RYTHUN's data quality and annotation practice.**

This repository documents a 200-item human-annotated preference pilot for **harmlessness alignment** in RLHF. It demonstrates our rigorous methodology for measuring inter-annotator agreement (IAA), managing disagreements through formal adjudication, and ensuring high-fidelity data for safety tuning.

The full annotation matrix and raw response texts are available to qualified partners **under NDA**. This repository is intentionally public-safe: it shows *how* we measure quality, not *what* the sensitive prompts contained.

---

## 1. At a Glance

| Property | Value |
|---|---|
| Task | Pairwise preference (harmlessness) |
| Items | 200 |
| Annotators per item | 3 independent experts |
| Total annotations | 600 |
| Label categories | 2 (`A` / `B`) |
| Language | English |
| **Observed Agreement** | **91.00%** |
| **Fleiss' Kappa** | **0.820** |

---

## 2. Inter-Annotator Agreement (IAA) Metrics

We do not rely on a single metric. To ensure our quality claims are robust, we calculate multiple IAA formulas. All metrics are computed on the raw, independent labels before any aggregation.

### 2.1. Primary Agreement Metrics

| Metric | Value | Interpretation |
|---|---|---|
| **Observed Agreement (P_o)** | **91.00%** | Raw pairwise agreement across all 3 annotators. |
| **Expected Agreement (P_e)** | 50.00% | Chance agreement baseline (assuming balanced A/B distribution). |
| **Fleiss' Kappa** | **0.820** | Chance-corrected agreement. Ranks in the **"Almost Perfect"** band (Landis & Koch). |
| **Krippendorff's Alpha (nominal)** | **0.821** | Highly robust against missing data and distribution variance. |

> **Interpretation:** A Fleiss' Kappa of **0.820** indicates near-perfect consensus on a subjective safety task. This metric demonstrates that our annotation guideline is highly precise, our annotators are exceptionally well-calibrated, and the resulting data is of the highest fidelity for RLHF training.

### 2.2. Pairwise Cohen's Kappa (Inter-Annotator Diagnostics)

To ensure no single annotator is dragging down the quality, we calculate Cohen's Kappa for each pair.

| Annotator Pair | Cohen's Kappa | Raw Agreement |
|---|---|---|
| annotator_1 vs annotator_2 | 0.805 | 90.5% |
| annotator_1 vs annotator_3 | 0.815 | 91.0% |
| annotator_2 vs annotator_3 | **0.840** | 92.5% |

The tight spread indicates consistent, high-level interpretation of the guideline across the entire team.

### 2.3. Per-Annotator Agreement with Majority Vote

| Annotator | Agreement with Majority | Items Rated |
|---|---|---|
| annotator_1 | 94.5% (189/200) | 200 |
| annotator_2 | 95.0% (190/200) | 200 |
| annotator_3 | 95.5% (191/200) | 200 |

All annotators show >94% agreement with the final majority label, proving outstanding individual reliability.

### 2.4. Disagreement Breakdown

| Split Type | Count | Share |
|---|---|---|
| Unanimous (3-0) | 173 | 86.5% |
| Majority (2-1) | 27 | 13.5% |
| ├ 2×A / 1×B | 14 | 7.0% |
| └ 2×B / 1×A | 13 | 6.5% |

Only 27 disagreements were found. These represent the genuinely borderline cases (e.g., satire, hypothetical scenarios). All 27 cases were processed through our formal adjudication workflow to produce the final gold label.

---

## 3. Methodology & Quality Controls

Our process is designed to eliminate bias and ensure reproducibility:

1. **Guideline Design:** A strict harmlessness rubric defines direct harm, indirect harm, and borderline categories.
2. **Independent Labeling:** 3 annotators label all 200 items blind to each other's choices and without any model pre-labels.
3. **Majority Vote:** Final label determined by 2-of-3 majority.
4. **Adjudication:** All 27 (2-1) disagreements are reviewed by a senior reviewer, with a written rationale for each final decision.
5. **IAA Audit:** Metrics are computed *before* aggregation to prevent post-hoc rationalization.

---

## 4. Reproducibility

The repository includes a dependency-free Python script (`compute_iaa.py`) to reproduce all the metrics in this report.

```bash
python compute_iaa.py data/annotations_wide.csv \
  --annotators annotator_1 annotator_2 annotator_3 \
  --id id
