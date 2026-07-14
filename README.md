# CSR: Contrastive Symbolic Regression

**Project page:** https://hengzhe-zhang.github.io/CSR-ICML/

This repository implements **"Contrastive Symbolic Regression: Aligned Representations, Adaptive Prediction, and Diverse Ensembles"** as presented in the ICML 2026 paper. CSR integrates evolutionary feature construction with contrastive learning and adaptive K-nearest neighbor regression for interpretable symbolic regression.

## 🌟 Overview

CSR addresses limitations in existing symbolic regression approaches by:

* 🔗 Aligning symbolic feature-space geometry with continuous target-space similarity
* 🧬 Using genetic programming to construct interpretable symbolic representations
* 📍 Applying adaptive K-nearest neighbor regression to model local residual structure
* 🧩 Combining global ridge regression with local KNN prediction
* 🎲 Using determinantal point process ensemble selection for diverse, robust models

## ✨ Key Features

* **Contrastive Symbolic Regression** 🎯: Learns symbolic feature spaces where nearby samples have similar target values
* **Closed-Form Alignment** ⚡: Uses an efficient closed-form contrastive transformation instead of expensive gradient optimization
* **Adaptive KNN** 🔍: Selects the neighborhood size automatically with efficient leave-one-out cross-validation
* **Linear-Rank Weighted KNN** 📈: Weights neighbors by rank to better evaluate representation quality during evolution
* **DPP Ensemble Selection** 🌲: Promotes high-quality and diverse symbolic models for stronger ensemble prediction

## 🚀 Installation

Note: This repository is provided as a lightweight project entry point. The implementation depends on the `EvolutionaryForest` package.

```bash
# Install the required base package
pip install git+https://github.com/hengzhe-zhang/EvolutionaryForest.git

# Install common scientific Python dependencies
pip install numpy scikit-learn
```

## 💻 Usage

Basic usage example:

```python
from CSR import est

# X_train, y_train, and X_test should be NumPy-compatible arrays
est.fit(X_train, y_train)

# Make predictions
predictions = est.predict(X_test)
```

You can also print the configured estimator directly:

```bash
python CSR.py
```

## ⚙️ Parameters

The default estimator in `CSR.py` is configured with:

* `n_gen`: Number of evolutionary generations
* `n_pop`: Population size
* `gene_num`: Number of symbolic features in each solution
* `base_learner`: Ridge-boosted linear-rank KNN learner
* `n_neighbors`: Adaptive KNN neighborhood selection
* `ensemble_selection`: DPP-based hall-of-fame ensemble selection
* `contrastive_l2_regularization`: L2 regularization strength for contrastive alignment
* `basic_primitives`: Symbolic operators used for feature construction

## 📚 Paper Summary

The paper argues that symbolic regression often focuses on explicit input-output equations while neglecting relational structure among samples. CSR instead evolves symbolic features whose distances reflect target similarity, making the learned representation useful for KNN-style local prediction and instance-level interpretability.

Experiments on 58 real-world regression datasets show that CSR consistently outperforms traditional symbolic regression methods and modern machine learning baselines.

## 📝 Citation

If you use this code in your research, please cite:

```bibtex
@inproceedings{zhang2026contrastive,
    title = {Contrastive Symbolic Regression: Aligned Representations, Adaptive Prediction, and Diverse Ensembles},
    author = {Zhang, Hengzhe and Chen, Qi and Xue, Bing and Banzhaf, Wolfgang and Zhang, Mengjie},
    booktitle = {Proceedings of the 43rd International Conference on Machine Learning},
    year = {2026},
    series = {PMLR},
    volume = {306}
}
```

## 📄 License

Add the appropriate license before distributing this repository. The copied method depends on external project code and should follow the licensing terms of those upstream dependencies.
