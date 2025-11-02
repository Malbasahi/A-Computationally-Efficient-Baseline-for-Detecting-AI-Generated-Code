## project
  title: "AI-Generated Code Detection (SemEval-2026 Task 13 Subtask A)"
  author: "Marwah Abdulqader Hasan Ba Suhai"
  affiliation: "Mohamed Bin Zayed University of Artificial Intelligence (MBZUAI)"
  course: "NLP701 – Fall 2025"
  kaggle_leaderboard_id: "Marwah Basuhai"
  public_macro_f1_score: 0.28224
  description: >
    A computationally efficient baseline for detecting AI-generated source code using 
    character-level n-gram hashing and logistic regression, developed as part of MBZUAI NLP701 
    Assignment 2 and SemEval-2026 Task 13 Subtask A.

---

## setup_instructions
  environment:
    install: "pip install -r requirements.txt"
    run_notebook: "jupyter notebook Assignment2.ipynb"
  regenerate_predictions:
    steps:
      - "Download dataset from Kaggle: https://www.kaggle.com/competitions/sem-eval-2026-task-13-subtask-a/data"
      - "Place it in data/Task_A/"
      - "Run all notebook cells"
      - "Generated file: artifacts/submission.csv"

---

## results_summary

| Metric       | Cross-Validation | Public Test (Kaggle) |
|--------------|------------------|----------------------|
| **Macro-F1** | 0.9555           | 0.28224              |
| **AUC**      | 0.9909           | —                    |

---

## methodology
  feature_engineering: "Character-level 3–5 n-grams hashed into 262k dimensions."
  classifier: "Logistic Regression (solver='saga', C=2.0, class_weight='balanced')."
  evaluation: "5-fold Stratified Cross-Validation optimized for Macro-F1."
  inference: "Probability threshold tuned to t* = 0.455 for F1 maximization."

---

## key_insights
  - "Character n-gram features effectively capture stylistic distinctions."
  - "Model overfits to the training domain; generalization drops across unseen languages."
  - "Future work: integrate semantic models (ASTs, CodeBERT) for deeper understanding."

---

## notes
  - "Dataset and kaggle.json are excluded for privacy and licensing reasons."
  - "Notebook assumes access to the Kaggle competition data."
  - "All experiments were conducted on CPU using Scikit-learn."

---

## acknowledgments
  - "Developed as part of MBZUAI NLP701: Advanced NLP."
  - "Task and dataset provided by the SemEval-2026 Task 13 organizers."

---

## references
  - "Bernecker, T., He, J., & Kumar, S. (2023). Detecting Machine-Generated Code in the Wild. arXiv:2311.04567."
  - "Frantzeskou, G., Stamatatos, E., Gritzalis, S., & Chaski, C. (2007). Source Code Author Identification Based on Byte-Level n-Grams. *JCSS, 72*(4):721–748."
  - "Krsul, I., & Spafford, E.H. (1997). Authorship Analysis: Identifying the Author of a Program. *Computers & Security, 16*(3):233–257."
  - "Weinberger, K.Q., Dasgupta, A., Langford, J., Smola, A.J., & Attenberg, J. (2009). Feature Hashing for Large Scale Multitask Learning. *ICML*."
  - "Fan, R.-E., Chang, K.-W., Hsieh, C.-J., Wang, X.-R., & Lin, C.-J. (2008). LIBLINEAR: A Library for Large Linear Classification. *JMLR, 9*:1871–1874."
  - "Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., Prettenhofer, P., Weiss, R., Dubourg, V., Vanderplas, J., Passos, A., Cournapeau, D., Brucher, M., Perrot, M., & Duchesnay, É. (2011). Scikit-learn: Machine Learning in Python. *JMLR, 12*:2825–2830."
  - "Nakov, P., & Briscoe, T. (2026). SemEval-2026 Task 13: Detecting AI-Generated Code. *Proceedings of SemEval*."
  - "SemEval-2026 Task 13 Organizers. (2025). Dataset available via Kaggle: https://www.kaggle.com/competitions/sem-eval-2026-task-13-subtask-a/data."
