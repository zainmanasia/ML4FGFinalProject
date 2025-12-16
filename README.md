# Exploring RNA-Binding Protein Interactions Using Transformer Models

## Overview

RNA-binding proteins (RBPs) play a critical role in post-transcriptional gene regulation, influencing RNA stability, localization, and translation. Accurate identification of RBP–RNA interactions is therefore an important problem in computational biology and functional genomics.

This project investigates the feasibility of using **transformer-based architectures** to model RNA–protein binding interactions, with a particular focus on:
- Evaluating predictive performance relative to established deep learning approaches
- Assessing whether **self-attention mechanisms** provide meaningful interpretability or insight for biological sequence analysis

Rather than aiming to outperform state-of-the-art models, this work focuses on understanding **where transformer models succeed, where they fail, and what they offer qualitatively** in the context of RBP prediction tasks.

---

## Background and Motivation

Recent advances in deep learning have led to successful applications in genomics and molecular biology, including models such as:
- **DeepBind**, which uses convolutional neural networks (CNNs) to predict binding preferences
- **iDeepS**, which combines CNNs with LSTMs to capture both sequence and structural dependencies

Transformers have achieved widespread success in natural language processing and have begun to see adoption in computational genomics. However, their effectiveness for RBP binding prediction—particularly compared to CNN-based architectures—remains an open question.

This project explores whether transformer encoders can:
1. Achieve competitive predictive performance
2. Provide biologically meaningful interpretability through attention mechanisms

---

## Dataset

Data was sourced from the **RNA-Binding Protein Database (RBPDB)**, using human-specific datasets derived from experimental RBP studies.

Each sample includes:
- RNA sequence
- Structural and thermodynamic features (e.g., MFE)
- Additional engineered descriptors (e.g., k-mer features)

Due to computational constraints, approximately **10% of the available dataset** was used for training and evaluation.

---

## Methods

### Data Processing

- Input sequences were standardized to a fixed length
- Data was split into training and testing sets using a **66/33 split**
- Only features relevant to binding prediction were retained

### Model Architecture

A **transformer encoder-only architecture** was implemented, consisting of:
- Token embedding and positional encoding
- Multi-head self-attention layers
- Feed-forward networks with normalization and dropout
- Fully connected output layers for prediction

The model leverages **scaled dot-product self-attention** to capture relationships between different regions of RNA sequences.

### Training Configuration

- Optimizer: Adam
- Learning rate scheduling applied
- Training performed for 20 epochs
- Evaluation metrics:
  - Accuracy
  - R-squared (R²)
  - Area Under the ROC Curve (AUC)

---

## Results

After 20 epochs, the model achieved:

- **Accuracy:** 65.96%
- **Loss:** 0.0775
- **R²:** 0.499
- **AUC:** 0.609

When compared to established models such as **iDeepS**, the transformer-based approach **underperformed in predictive accuracy**, which is consistent with prior findings favoring convolutional architectures for this task.

---

## Attention-Based Visualization

Although predictive performance lagged behind CNN-based models, the transformer architecture enabled **attention-based visualization** of sequence interactions.

The attention mechanism allows:
- Construction of attention matrices
- Visualization of relationships between different sequence positions
- Qualitative inspection of regions potentially important for binding behavior

These visualizations provide an interpretable view of model behavior, though their biological utility remains exploratory.

---

## Discussion

This work highlights several important observations:

- Transformer models, in their current form, do not outperform CNN-based architectures for RBP binding prediction
- The limited dataset size likely constrained transformer performance
- Self-attention mechanisms offer interpretability but **do not translate into improved predictive accuracy**
- CNN-based models remain better suited for this task due to their inductive bias toward local sequence patterns

Importantly, this project underscores the need to **evaluate ML architectures critically rather than assume transferability across domains**.

---

## Conclusion

Transformer models provide a flexible and interpretable framework for modeling biological sequences, but for RNA-binding protein interaction prediction, **traditional deep learning architectures currently offer superior performance**.

The primary contribution of this work lies in:
- Empirically evaluating transformer feasibility for RBP tasks
- Demonstrating attention-based visualization capabilities
- Providing a balanced assessment of strengths and limitations

Future advances may improve transformer efficacy in this domain, but at present, convolutional approaches remain the practical choice.

---

## Code

Implementation and experiments are available at:  
👉 https://github.com/zainmanasia/ML4FGFinalProject.git

---

## References

- Chandra A. et al. (2023). *Transformer-based deep learning for predicting protein properties*. eLife.
- Clauwaert J. et al. (2021). *Explainability in transformer models for functional genomics*. Briefings in Bioinformatics.
- Ding Y. et al. (2022). *Time–frequency transformer for fault diagnosis*. MSSP.
- Moore K.S., ’t Hoen P.A.C. (2019). *Computational approaches for RNA–protein interactions*. JBC.
- Nikam R., Gromiha M.M. (2019). *Seq2Feature*. Bioinformatics.
- Zhang S. et al. (2023). *Transformer-based language models in bioinformatics*. Bioinformatics Advances.
- RBPDB: https://rbpdb.ccbr.utoronto.ca
