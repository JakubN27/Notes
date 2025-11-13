# 🧭 COMP2261 Machine Learning Coursework — Day-by-Day Checklist

**Deadline:** Tuesday, 16 December 2025, 14:00  
**Estimated total time:** ~20 hours  

---

# 🧭 COMP2261 Machine Learning Coursework — Advanced Day-by-Day Plan

**Module:** COMP2261 Artificial Intelligence  
**Coursework:** Machine Learning Coursework  
**Credits:** 10 | **Weight:** 50% of module mark  
**Deadline:** Tuesday, 16 Dec 2025, 14:00  
**Estimated hours:** ~20  
**Submission:** Ultra ([CIS_username].zip, [CIS_username].pdf)  

**Goal:** Achieve advanced marks by implementing **custom models**, exploring **few-shot/zero-shot paradigms**, and performing **multi-modal analysis**.

---

## Week 1 — Data Exploration & Paradigm Design (Nov 11–17) ✅ 25%
**Goal:** Thorough dataset understanding + plan advanced paradigm.

| Date | Task |
|------|------|
| **Mon, Nov 11** | Load BraVL dataset, inspect structure, number of samples, classes, image/text modalities. |
| **Tue, Nov 12** | Analyse class distribution, identify imbalance, explore numeric/embedding features. |
| **Wed, Nov 13** | Plot histograms, scatter plots, and heatmaps; visualise sample image–text pairs. |
| **Thu, Nov 14** | Explore multi-modal embeddings (text + image) for potential zero-shot/few-shot use. |
| **Fri, Nov 15** | Draft **Data & Paradigm** section: justify 70/30 split and propose advanced paradigm (few-shot/zero-shot). |
| **Sat, Nov 16** | Refine visualisations; write paragraph linking dataset characteristics to potential biases and generalisation limits. |
| **Sun, Nov 17** | Ensure Week 1 deliverables ready for report (plots + text). |

---

## Week 2 — Baseline Model Development (Nov 18–24) ✅ 25%
**Goal:** Train and evaluate supervised baseline; set comparison for custom model.

| Date | Task |
|------|------|
| **Mon, Nov 18** | Choose baseline model (Logistic Regression, SVM, KNN). Prepare train/test split (70/30) and optional validation split. |
| **Tue, Nov 19** | Implement baseline using scikit-learn; train and predict on test set. |
| **Wed, Nov 20** | Compute metrics: accuracy, precision, recall, F1; generate confusion matrix heatmap. |
| **Thu, Nov 21** | Optional: hyperparameter tuning (regularisation, kernel) for improved baseline. |
| **Fri, Nov 22** | Summarise results in metrics table; draft comparison notes for report. |
| **Sat, Nov 23** | Add figures linking baseline trends to dataset characteristics (e.g., class imbalance). |
| **Sun, Nov 24** | Finalise baseline section for **Model Development** (include discussion of methodology + results). |

---

## Week 3 — Custom Model Class (Nov 25–Dec 1) ✅ 25%
**Goal:** Implement model from scratch; improve and compare performance; explore advanced improvements.

| Date | Task |
|------|------|
| **Mon, Nov 25** | Decide on custom model: KNN (distance weighting, normalisation) or Logistic Regression (manual gradient descent). |
| **Tue, Nov 26** | Implement `fit()` and `predict()` methods; validate small test examples. |
| **Wed, Nov 27** | Run full dataset; compute metrics (accuracy, F1) and compare to sklearn baseline. |
| **Thu, Nov 28** | Implement optional advanced improvements: weighted KNN, normalization, early stopping, gradient tuning. |
| **Fri, Nov 29** | Visualise comparison (tables, plots) of baseline vs custom model. |
| **Sat, Nov 30** | Write paragraph on differences, lessons learned, and performance justification. |
| **Sun, Dec 1** | Ensure **Custom Model Implementation** section ready for report. |

---

## Week 4 — Advanced Paradigm + Report Writing (Dec 2–15) ✅ 25%
**Goal:** Run few-shot/zero-shot experiment; write full LaTeX report; finalise submission.

| Date | Task |
|------|------|
| **Mon, Dec 2** | Decide advanced paradigm (few-shot, zero-shot, or hybrid); plan dataset split. |
| **Tue, Dec 3** | Prepare train/test (or train/unseen) split; include embeddings for zero-shot if needed. |
| **Wed, Dec 4** | Train advanced model; collect predictions, metrics. |
| **Thu, Dec 5** | Generate visualisations: confusion matrix, t-SNE embeddings, error analysis. |
| **Fri, Dec 6** | Draft **Results Analysis** paragraph: compare baseline, custom, and advanced paradigms; discuss generalisation, biases, and real-world implications. |
| **Sat, Dec 7** | Begin LaTeX report: title, abstract, intro, related work (cite Long 2017, 2018; Pu 2023; Duan 2023). |
| **Sun, Dec 8** | Write **Data & Paradigm** section (include Week 1 visuals + advanced paradigm justification). |
| **Mon, Dec 9** | Write **Model Development** section (baseline + custom + advanced). |
| **Tue, Dec 10** | Update results with final metrics, visualisations; add commentary linking dataset exploration to model behaviour. |
| **Wed, Dec 11** | Draft **Result Analysis** section; include qualitative insights, ablation or error analysis. |
| **Thu, Dec 12** | Proofread full report, check figure captions, tables, references, and formatting. |
| **Fri, Dec 13** | Compile PDF `[CIS_username].pdf`. |
| **Sat, Dec 14** | Zip all code `[CIS_username].zip`. |
| **Sun, Dec 15** | Final review; ensure PDF + zip ready for Ultra submission. |

---

### ✅ Advanced Mark Checklist
- Implement **custom model from scratch** (not starter code).  
- Include **few-shot/zero-shot or hybrid paradigm**.  
- Multi-modal exploration (image + text embeddings) recommended.  
- Visualise with **heatmaps, t-SNE embeddings, error analysis**.  
- Provide **clear discussion linking dataset, paradigm, and model performance**.  
- Optional: ablation study or advanced method improvement for extra credit.
