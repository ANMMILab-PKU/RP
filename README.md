# Enhancing Uncertainty Assessment in Dynamic PET Imaging with Residual Permutation and Clustering

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Python 3.x](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)

This repository contains the official implementation of the paper: **"Enhancing Uncertainty Assessment in Dynamic PET Imaging with Residual Permutation and Clustering"**. 

In this work, we propose a novel **Residual Permutation (RP)** framework for robust uncertainty quantification in dynamic Positron Emission Tomography (PET) imaging. The repo also includes implementations of two state-of-the-art baseline methods: **Bootstrap** and **MCMC**.

## 📝 Overview

Quantitative PET relies on robust uncertainty quantification to ensure the reliability of estimated kinetic parameters. Existing methods like Bayesian MCMC are computationally expensive, Bootstrap is noise-sensitive, and Deep Learning approaches require large datasets and often lack physical scale sensitivity. 

To address these challenges, our **Residual Permutation (RP)** method:
1. **Clusters** Time-Activity Curves (TACs) using K-means to group kinetically homogeneous regions.
2. **Fits** a Linear Mixture Model utilizing **Huber loss** and **Elastic Net** regularization to prevent overfitting to noise.
3. **Permutes residuals** within each cluster to generate pseudo-PET images, preserving spatiotemporal noise characteristics.
4. **Estimates uncertainty** of kinetic parameters (using 2TCM) efficiently, distribution-free, and without the need for training data.

## 📂 Repository Structure

The code is organized into three main directories:

```text
├── residual_permutation/    # Our proposed method
│   ├── ...                  # Core scripts for K-means, fitting, and permutation
├── baseline_Bootstrap/      # Baseline 1: Bootstrap-based approach (O'Sullivan et al.)
│   ├── ...                  
├── baseline_MCMC/           # Baseline 2: Markov Chain Monte Carlo approach
│   ├── ...                  
└── README.md
```


## 🚀 Usage

### 1. Run the Proposed Method (Residual Permutation)
Navigate to the proposed method directory and run the main script. The script will cluster the TACs, fit the regularized model, perform residual permutations, and output the uncertainty estimation.

```bash
cd residual_permutation
```

### 2. Run Baselines
To compare the results, you can run the provided baseline methods on the same data.

**Run Bootstrap Baseline:**
```bash
cd ../baseline_Bootstrap
```

**Run MCMC Baseline:**
```bash
cd ../baseline_MCMC
```

## 📊 Key Results

Compared to the MCMC and Bootstrap baselines, our RP method provides:
* **Higher consistency** with varying noise levels (strong linear correlation between noise and uncertainty).
* **Robustness** against high-intensity noise and outliers, maintaining physical interpretability.
* **Higher computational efficiency** compared to MCMC, making it a highly deployable solution for voxel-wise whole-body parametric analysis.


## 🔗 Citation

If you find this code or our proposed RP method useful in your research, please consider citing our paper:

```bibtex
@article{ma2024enhancing,
  title={Enhancing Uncertainty Assessment in Dynamic PET Imaging with Residual Permutation and Clustering},
  author={Ma, Kun and Cheng, Fangxiao and Liu, Wei and Shao, Wenrui and Yang, Yalei and Li, Nan and Meng, Xiangxi and Xie, Zhaoheng},
  journal={Preprint submitted to Elsevier},
  year={2024}
}
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ✉️ Contact

For any questions, feel free to open an issue or contact the corresponding authors:
* Xiangxi Meng (mengxiangxi@pku.edu.cn)
* Zhaoheng Xie (xiezhaoheng@pku.edu.cn)
