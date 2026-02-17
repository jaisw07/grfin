# Fairness-Aware Glaucoma Detection using Deep Learning

A deep learning framework for **glaucoma diagnosis from OCT RNFL images**, designed to achieve **strong diagnostic performance while maintaining fairness across demographic groups**.

This project introduces a regularization-enhanced architecture that improves **generalization and subgroup robustness** without relying on explicit demographic conditioning.

---

## 🚩 Problem Statement

Glaucoma is one of the leading causes of irreversible blindness. Early detection using Optical Coherence Tomography (OCT) imaging is crucial.

However, many medical AI systems show **performance disparities across demographic groups**, raising concerns about fairness and real-world deployment.

This work investigates:

* Can we build a **high-performing glaucoma classifier**?
* Can fairness improve **without explicitly using demographic information**?
* Can architectural regularization improve subgroup robustness?

---

## 🧠 Proposed Approach

We develop **StochDepth-ResNet18**, a modified ResNet18 architecture with enhanced regularization:

### Model Enhancements

* Single-channel OCT input adaptation
* Stochastic depth in residual blocks
* Stage-wise dropout
* Gaussian noise augmentation
* Gradient clipping for stable training

The goal is to force the model to learn **stable structural features** rather than demographic-specific patterns.

---

## 📊 Dataset

Experiments use the **Harvard Glaucoma Fairness Dataset**, containing:

* 3,300 OCT RNFL scans
* Balanced demographic distribution
* Race groups: Asian, Black, White
* Predefined train/validation/test splits

This makes the dataset ideal for fairness analysis.

---

## 📈 Results

### Diagnostic Performance

| Metric    | Value  |
| --------- | ------ |
| Accuracy  | 76.78% |
| Precision | 0.815  |
| Recall    | 0.740  |
| F1 Score  | 0.776  |
| ROC-AUC   | 0.8538 |

### Fairness Metrics

| Metric                        | Value  |
| ----------------------------- | ------ |
| Equity-Scaled Accuracy        | 75.00  |
| Equity-Scaled AUC             | 83.28  |
| Demographic Parity Difference | 13.33% |
| Equalized Odds Difference     | 8.31%  |

The model achieves competitive fairness compared to fairness-conditioned baselines while **not using demographic labels**.

---

## ⚙️ Training Details

* Framework: PyTorch
* Loss: BCEWithLogitsLoss
* Optimizer: AdamW
* LR Scheduler: StepLR
* Regularization:

  * Dropout
  * Stochastic Depth
  * Gaussian Noise
* Gradient clipping: max norm = 1.0

---

## 🔬 Key Insights

* Regularization improves **both performance and fairness**.
* Fairness gains can emerge from **better generalization**, not only fairness-aware losses.
* Stable features reduce subgroup disparities.

---

## 👥 Authors

* Shrey Jaiswal
* Gaurav Ghosh
* Vanshita Mehta
