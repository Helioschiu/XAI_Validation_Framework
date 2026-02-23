# XAI Validation Framework for Clinical Gait Analysis

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.9+-ee4c2c.svg)](https://pytorch.org/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

---

## 📋 Overview

This repository contains the official implementation of:

> **"Evaluating Plausibility of Explainable AI in Clinical Gait Analysis: A Framework using Sensitivity, Faithfulness, and Cross-Method Coherence"**  
> *(Under review)*

The framework evaluates post-hoc explainable AI (XAI) methods applied to deep learning models trained on three-dimensional clinical gait analysis (3D-CGA) data.

Explanations are assessed across three complementary dimensions:

- **Sensitivity**
- **Faithfulness**
- **Cross-method Coherence**

All experiments are implemented in a single Google Colab notebook.

---

## 📂 Repository Contents

```
xai_validation_framework.ipynb
README.md
```

The notebook contains the complete pipeline:

- Data loading
- 1D-CNN model training
- XAI attribution generation (Captum + Zennit)
- Sensitivity testing (progressive masking)
- Weight and label randomisation tests
- Cross-method coherence analysis
- Heatmap visualisation

---

## 📊 Dataset

The framework was demonstrated on a binary classification task:

**Idiopathic Toe Walking (ITW)** vs **Typically Developing (TD)** gait.

### Expected Input Format

The notebook expects a dataset with:

- Input shape: `(N_samples, 8, 101)`
- 8 joint angle trajectories
- 101 time points per stride
- Labels shape: `(N_samples,)`

⚠️ The dataset is **not included** in this repository.

You must configure your own dataset path inside the notebook, e.g.:

```python
DATA_PATH = "/content/your_dataset.npz"
```

The `.npz` file should contain:

```python
X  # input array
y  # labels
```

If your dataset structure differs, modify the loading cell accordingly.

---

## 🚀 How to Use (Google Colab)

1. Upload `xai_validation_framework.ipynb` to Google Colab.
2. Upload your dataset file (`.npz`) to Colab or mount Google Drive.
3. Update the `DATA_PATH` variable inside the notebook.
4. Run all cells sequentially.

All dependencies are installed within the notebook.

---

## 🧪 What the Notebook Performs

### ✅ Model Training
- 1D-CNN for stride-level classification
- Subject-level cross-validation

### ✅ Sensitivity Analysis
- Progressive masking of top-attributed regions
- AUROC decline curves
- Comparison against random masking baseline

### ✅ Faithfulness Testing
- Progressive weight randomisation
- Progressive label corruption
- Spearman correlation and Jaccard overlap decay

### ✅ Cross-Method Coherence
- Pairwise similarity matrices
- Drop-one-method ablation
- Global overlap metrics

### ✅ Visualisation
- Mean relevance heatmaps per XAI method
- Combined heatmap for biomechanical interpretation

---

## 📄 Citation

If you use this framework in your research, please cite:


---

## 📬 Contact

For questions or collaborations:  
[ching.chiu@ndorms.ox.ac.uk]

---

## 📝 License

MIT License
