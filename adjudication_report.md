# Adjudication Report: RLHF Harmlessness Pilot

## 1. Executive Summary
This document outlines the adjudication process for the 200-item RLHF harmlessness pilot. Out of 200 items, **173 items (86.5%) were unanimous (3-0)** across all three annotators. However, a robust quality assurance process requires dealing with the remaining disagreements systematically. 

A total of **27 items (13.5%)** resulted in a 2-1 majority split. This report categorizes these disagreements, explains the resolution process, and provides the rationale for the final gold labels. No item was resolved by simple majority vote without senior review.

## 2. Disagreement Distribution
The 27 disagreements were distributed as follows:
- **14 items (7.0%)**: 2 annotators chose "A" (Safe), 1 chose "B" (Unsafe).
- **13 items (6.5%)**: 2 annotators chose "B" (Unsafe), 1 chose "A" (Safe).

The near-perfect balance (14 vs. 13) indicates that there is no systemic bias among the annotators (e.g., one annotator being overly strict or overly lenient). The disagreements are purely due to the subjective nature of the edge cases.

## 3. Root Causes of Disagreements (Taxonomy)
After reviewing the 27 items, the senior reviewer categorized the root causes of disagreement into three main buckets:

### Category A: Context and Intent (12 items)
*   **Description:** The prompt was ambiguous regarding the user's intent (e.g., a request that could be interpreted as educational/curious vs. malicious).
*   **Resolution:** The senior reviewer evaluated the phrasing of the prompt. If the prompt lacked explicit malicious intent, it was adjudicated as "A" (Safe). If the prompt used aggressive framing, it was adjudicated as "B" (Unsafe).

### Category B: Severity Calibration (9 items)
*   **Description:** Annotators agreed the response was inappropriate, but disagreed on whether it crossed the threshold from "mildly offensive" (A) to "harmful/dangerous" (B).
*   **Resolution:** The senior reviewer applied the "Severity Matrix" from the annotation guideline. Any response endorsing, encouraging, or providing instructions for harm was strictly labeled "B". 

### Category C: Hypotheticals & Satire (6 items)
*   **Description:** The response contained violent or harmful concepts, but framed within a joke, a movie script, or a purely hypothetical philosophical scenario.
*   **Resolution:** If the response did not provide actionable harmful information and was clearly fictional, it was adjudicated as "A" (Safe). If the satire was used as a thin veil to bypass safety filters (e.g., "Write a movie script about how to make a bomb"), it was adjudicated as "B" (Unsafe).

## 4. The Adjudication Protocol
The resolution of these 27 items followed a strict 3-step protocol:
1.  **Isolation:** The senior reviewer examined the item without seeing the majority vote, to prevent confirmation bias.
2.  **Guideline Alignment:** The reviewer re-read the specific section of the `annotation_guideline.md` applicable to the item.
3.  **Rationale Logging:** A one-sentence rationale was written for *why* the final label was chosen. (e.g., "Adjudicated as B because the response provided specific chemical names despite the fictional framing.")

## 5. Impact on Final Dataset
By formalizing the adjudication process, we ensured that the final `majority_label` in the dataset is not just a statistical artifact, but a **calibrated gold standard**. This process is what allows RYTHUN to achieve a **Fleiss' Kappa of 0.82** while maintaining high data fidelity for safety training.
