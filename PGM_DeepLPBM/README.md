# MVA2025_PGM_DeepLPBM

# Deep Latent Position Block Model (Deep LPBM) — Reimplementation & Extensions of Boutin et al. (2025)

Studied paper: https://doi.org/10.1007/s11222-025-10679-7
Further explaination: https://hal.science/hal-04910241v1/document

## Overview

This repository provides a full **from-scratch reimplementation** of the **Deep Latent Position Block Model (Deep LPBM)** introduced by Boutin et al. (2025). Deep LPBM is a probabilistic framework that jointly performs **block clustering** and **latent space visualization** of networks by combining block models with deep variational graph autoencoders.

Beyond reproducing the original method, this project critically analyzes its empirical behavior, highlights reproducibility challenges, and proposes an **extension to directed graphs with self-loops** using an attention-based encoder.

All experiments are implemented as **fully executable Jupyter/Colab notebooks**.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](
https://colab.research.google.com/drive/1PAQlR8zzE5LCQtk4NygP6cVYdwNgRhDp?usp=sharing
)
---

## Abstract

This document summarizes, contextualizes, and investigates the framework for studying graph-structured data proposed by Boutin et al. \cite{boutin2025deep}. They introduced a novel model, the Deep Latent Position Block Model (Deep LPBM), that simultaneously performs node clustering and interpretable visualization of the network in a latent space. The model is claimed to capture diverse connectivity structures and estimate partial node memberships. In this work, we present a full re-implementation of the Deep LPBM framework from scratch. Furthermore, we propose an extension of the model designed to capture directed graph structures, including self-loops. Our experiments demonstrate that this extension effectively models asymmetric connectivity while maintaining performance comparable to the original architecture on undirected graphs.

---



---

## Notebooks

Each notebook is self-contained and can be run independently.

- **`Deep_LPBM_v2.ipynb`**  
  Core reimplementation of the original Deep LPBM for **undirected graphs**, including pretraining, variational inference, clustering evaluation, and latent-space visualization.

- **`Ego_v2_Deep_LPBM_v2.ipynb`**  
  Application of Deep LPBM to **real-world ego-network data** (SNAP Facebook dataset), with analysis of model selection, visualization limits, and empirical shortcomings.

- **`Asymmetric_Deep_LPBM_v2.ipynb`**  
  **Extension to directed graphs with self-loops**, removing symmetry constraints on the connectivity matrix and replacing the GCN encoder with a GAT.

- **`Deep_LPBM_Frobenius_norm_comparison.ipynb`**  
  Quantitative evaluation of **connectivity matrix recovery**, comparing initialization versus trained estimates using the Frobenius norm across graph types and parameters.

---

## Key Findings & Contributions

- Complete independent reimplementation of Deep LPBM without access to official source code.
- Empirical evidence of **high sensitivity to initialization and pretraining**.
- Observation that connectivity estimates may **degrade during training**, despite improving t-SNE visualization.
- Demonstration that **larger sample sizes** are required to reproduce the performance claimed in the original paper.
- Successful extension of Deep LPBM to **directed networks**, preserving clustering and visualization quality.

---

## Reproducibility & Known Issues

This repository aims to be transparent about reproducibility limitations observed during the study.

- Results are **highly sensitive** to:
  - initialization of the connectivity matrix  
  - pretraining duration  
- Frobenius norm recovery of the connectivity matrix often **worsens after training** compared to initialization.
- Performance reported in the original paper could not be consistently reproduced under the stated experimental settings (e.g. Beta=0.3,N=200).
- Several **ambiguities and inconsistencies** were identified in the published manuscript (e.g. variance parameterization, initialization loss definition).
- On dense real-world graphs, visualization and model selection (AIC) become unreliable, while (BIC) never provided good results.

These issues are discussed in detail in the accompanying report and illustrated directly in the notebooks.

---

## Requirements & Execution

The notebooks are designed to run on **Google Colab** or locally with Python ≥ 3.9.
For Colab, dependencies are installed directly inside the notebooks.

---

## Authors

- **Yannaël Bossard**  
  ENS Paris-Saclay  
- **Karina Musina**  
  CentraleSupélec  

Both authors contributed to the code and experimental analysis.

---

## License

This repository is released for **academic and research purposes**.





