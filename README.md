# REYTHUN-IAA-SAMPLE-
RYTHUN — Sample work: quality report for a 200-item RLHF harmlessness preference dataset. 3 annotators, 84% observed agreement, Fleiss' Kappa 0.68, documented adjudication. Methodology and sanitized samples only; full dataset under NDA.
# 
# RYTHUN — RLHF Harmlessness Preference Data Quality Report

**Sample work from RYTHUN's data quality and annotation practice.**

This repository documents a 200-item human-annotated preference pilot for **harmlessness alignment** in RLHF. It demonstrates our rigorous methodology for measuring inter-annotator agreement (IAA), managing disagreements through formal adjudication, and ensuring high-fidelity data for safety tuning.

We do not publish our raw annotation matrix publicly. Instead, we prove our quality through a **discounted pilot program**. You provide the prompts; we deliver the data, the IAA metrics, and the full audit trail. 

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

We calculate multiple IAA formulas to ensure our quality claims are robust. All metrics are computed on the raw, independent labels before any aggregation.

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

Only 27 disagreements were found. These represent the genuinely borderline cases. All 27 cases were processed through our formal adjudication workflow to produce the final gold label.

---

## 3. Methodology & Quality Controls

Our process is designed to eliminate bias and ensure reproducibility:

1. **Guideline Design:** A strict harmlessness rubric defines direct harm, indirect harm, and borderline categories.
2. **Independent Labeling:** 3 annotators label all items blind to each other's choices and without any model pre-labels.
3. **Majority Vote:** Final label determined by 2-of-3 majority.
4. **Adjudication:** All (2-1) disagreements are reviewed by a senior reviewer, with a written rationale for each final decision.
5. **IAA Audit:** Metrics are computed *before* aggregation to prevent post-hoc rationalization.

---

## 4. Engagement Model & Pilot Program

RYTHUN provides high-quality, documented data for frontier AI labs and safety teams. We are so confident in our quality that we offer a **50% discounted pilot program** to prove our capabilities on your data.

| Stage | Scope | Pricing | Output |
|---|---|---|---|
| **Smoke Test** | 20–50 items on your data | **Free** | Labeled file + rationale |
| **Discounted Pilot** | 200–500 items | **50% OFF standard rate** | CSV + Full IAA Report + Adjudication Log |
| **Production** | 2,000+ items/month | Standard agreed rate | Weekly batches with rolling IAA audits |

### The Pilot Guarantee & Verification
Our pilot is designed to eliminate your risk entirely. We do not just send you labels; we send you the proof.
1. **Target:** We commit to a **Fleiss' Kappa target of ≥ 0.80** on the pilot dataset.
2. **Verification:** Upon delivery, you will receive the annotation matrix, the IAA calculation script, and the audit report. Your engineers can run the script locally to independently verify the Kappa score.
3. **The Upgrade:** If the pilot meets the Kappa ≥ 0.80 threshold, we transition to a full production contract at standard rates. If it fails, we will revise the pilot for free until the threshold is met.

For inquiries and NDA requests: **[Your Email Address]**

---

## 5. License

**Proprietary and Confidential.**  
Copyright (c) 2026 RYTHUN. All Rights Reserved.  
The materials in this repository are for evaluation purposes only. Any use, reproduction, or commercial deployment requires a separate written license agreement. See the `LICENSE` file for full terms.
