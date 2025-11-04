## project
  Title: "AI-Generated Code Detection (SemEval-2026 Task 13 Subtask A)"
  author: "Marwah Abdulqader Hasan Ba Suhai"
  affiliation: "Mohamed Bin Zayed University of Artificial Intelligence (MBZUAI)"
  course: "NLP701 – Fall 2025"
  kaggle_leaderboard_id: "Marwah Basuhai"
  public_macro_f1_score: 0.45033
  description: >
    A reproducible and computationally efficient baseline for detecting AI-generated
    source code using character-level TF-IDF n-grams and balanced logistic regression.
    Developed as part of MBZUAI NLP701 Assignment 2 and SemEval-2026 Task 13 Subtask A.

---

## setup_instructions
  environment:
    install: "pip install -r requirements.txt"
    run_notebook: "jupyter notebook Assignment2.ipynb"
  regenerate_predictions:
    steps:
      - "Download the dataset from Kaggle: https://www.kaggle.com/competitions/sem-eval-2026-task-13-subtask-a/data"
      - "Place it under data/Task_A/"
      - "Run all notebook cells sequentially"
      - "Generated file: artifacts/submission.csv (columns: ID,label)"

---

## results_summary

| Class      | Precision | Recall | F1-score | Support |
|-------------|------------|---------|-----------|----------|
| **Human (0)**   | 0.9523 | 0.9549 | 0.9536 | 238 475 |
| **Machine (1)** | 0.9588 | 0.9564 | 0.9576 | 261 525 |
| **Accuracy**    | — | — | **0.9556** | 500 000 |
| **Macro Avg**   | 0.9555 | 0.9556 | 0.9556 | 500 000 |
| **Weighted Avg**| 0.9557 | 0.9556 | 0.9557 | 500 000 |

**Cross-validation macro-F1:** 0.9556 | **Public Kaggle macro-F1:** 0.45033 | **Threshold (t₍final₎):** 0.485

---

## methodology
  feature_engineering: >
    Character-level TF-IDF n-grams (3 – 5 range) with up to 1 million features.
    The representation captures indentation, operator spacing, and naming style
    while down-weighting frequent patterns via inverse document frequency.
  classifier: >
    Logistic Regression (solver = 'saga', C = 2.0, class_weight = 'balanced').
  evaluation: >
    5-fold Stratified Cross-Validation optimized for Macro-F1, followed by threshold
    calibration on the public validation split.
  inference: >
    Probability threshold t\_final = 0.485 chosen on the validation set
    (no polarity flip required).

---

## key_insights
  - "TF-IDF character n-grams capture robust stylistic cues distinguishing human from AI-generated code."
  - "The model generalizes well on the validation set (Macro-F1 ≈ 0.955) but drops on the hidden Kaggle test, indicating domain shift."
  - "Future work: incorporate semantic context (ASTs, CodeBERT) for cross-domain generalization."

---

## notes
  - "Dataset and kaggle.json are excluded for privacy and licensing reasons."
  - "Notebook assumes prior access to the official Kaggle competition data."
  - "All experiments executed on CPU (12-core) using Scikit-learn 0.24+, Python 3.10."
  - "Training time ≈ 5 minutes for 500 k samples; inference < 1 ms per snippet."

---

## acknowledgments
  - "Developed as part of MBZUAI NLP701: Advanced NLP."
  - "Task and dataset provided by the SemEval-2026 Task 13 organizers."

---

## references
  - "Bernecker, T., He, J., & Kumar, S. (2023). Detecting Machine-Generated Code in the Wild. arXiv:2311.04567."
  - "Frantzeskou, G., Stamatatos, E., Gritzalis, S., & Chaski, C. (2007). Source Code Author Identification Based on Byte-Level n-Grams. *JCSS, 72*(4): 721–748."
  - "Krsul, I., & Spafford, E.H. (1997). Authorship Analysis: Identifying the Author of a Program. *Computers & Security, 16*(3): 233–257."
  - "Fan, R.-E., Chang, K.-W., Hsieh, C.-J., Wang, X.-R., & Lin, C.-J. (2008). LIBLINEAR: A Library for Large Linear Classification. *JMLR, 9*: 1871–1874."
  - "Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., Prettenhofer, P., Weiss, R., Dubourg, V., Vanderplas, J., Passos, A., Cournapeau, D., Brucher, M., Perrot, M., & Duchesnay, É. (2011). Scikit-learn: Machine Learning in Python. *JMLR, 12*: 2825–2830."
  - "Nakov, P., & Briscoe, T. (2026). SemEval-2026 Task 13: Detecting AI-Generated Code. *Proceedings of SemEval*."
  - "SemEval-2026 Task 13 Organizers (2025). Dataset available via Kaggle: https://www.kaggle.com/competitions/sem-eval-2026-task-13-subtask-a/data."
