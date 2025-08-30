# Constrained Deep Clustering of scRNA-seq Data with Limited Domain Knowledge

This repository contains the implementation, datasets, and results for the MSc dissertation project on **Constrained Deep Clustering of scRNA-seq data**. The project benchmarks classical and deep clustering algorithms, including **K-means**, **Deep Embedded Clustering (DEC)**, and the semi-supervised **single-cell Deep Constrained Clustering (scDCC)**.  

The central idea is to evaluate how **limited domain knowledge** (in the form of pairwise constraints: must-link and cannot-link) improves clustering accuracy, interpretability, and robustness for single-cell RNA sequencing (scRNA-seq) datasets.  

---

## 📑 Table of Contents
1. [Project Overview](#project-overview)  
2. [Repository Structure](#repository-structure)  
3. [Datasets](#datasets)  
4. [Installation & Requirements](#installation--requirements)  
5. [Usage](#usage)  
6. [Results](#results)  
7. [Contact](#contact)  

---

## 📘 Project Overview
Single-cell RNA sequencing (scRNA-seq) enables profiling of thousands of individual cells to study heterogeneity in tissues. However, clustering scRNA-seq data is challenging due to:  
- **High dimensionality** (thousands of genes per cell),  
- **Sparsity** (dropout zeros in expression values), and  
- **Noisy biological variation**.  

### Methods Benchmarked
- **K-means** — baseline unsupervised clustering.  
- **DEC (Deep Embedded Clustering)** — learns embeddings with a deep autoencoder.  
- **scDCC (single-cell Deep Constrained Clustering)** — incorporates limited domain knowledge via pairwise constraints (must-link/cannot-link).  

### Evaluation Metrics
- **Normalized Mutual Information (NMI)**  
- **Adjusted Rand Index (ARI)**  
- **Clustering Accuracy (CA)**  

---

## 📂 Repository Structure

```
project/
├── dataset/
│   ├── Mouse_bladder_data.h5
│   ├── pbmc4k_raw_gene.h5
│   ├── Worm_neuron_raw_data.h5
│   └── GSE84133_RAW/               # Baron Human Pancreas raw CSVs
│
├── processed_dataset/
│   ├── mouse_bladder_preprocessed.h5ad
│   ├── pbmc4k_preprocessed.h5ad
│   ├── worm_neuron_preprocessed.h5ad
│   └── baron_pancreas_preprocessed.h5ad
│
├── results/
│   └── {dataset_name}/
│       ├── *_comparison_plot_final.png
│       ├── *_scDCC.png
│       └── *_umap_constraints_final.png
│
├── dash_data/
│   ├── Baron Pancreas/
│   ├── Mouse Bladder/
│   ├── PBMC 4k/
│   └── Worm Neuron/
│
├── preprocessing_*.ipynb           # dataset-specific preprocessing notebooks
├── algorithm.ipynb                 # model training/evaluation (K-means, DEC, scDCC)
├── Presentation.ipynb              # presentation visuals
├── requirements.txt
└── README.md
```

---

## 📦 Datasets
The project uses four benchmark scRNA-seq datasets:

- **Baron Human Pancreas (GSE84133):**  
  [Link](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE84133)  

- **Mouse Bladder & Worm Neuron (from scDCC study):**  
  [Link](https://figshare.com/articles/dataset/scDCC_data/21563517?file=38224590)  

- **PBMC 4k (10x Genomics):**  
  [Link](https://www.10xgenomics.com/datasets/4-k-pbm-cs-from-a-healthy-donor-2-standard-2-1-0)  

Raw datasets are stored under `dataset/`, and preprocessed files are saved in `processed_dataset/`.

---

## ⚙️ Installation & Requirements

### Clone the repository
```bash
git clone https://github.com/KashifMoin1410/Constrained-Deep-Clustering-of-scRNA-seq-Data-with-Limited-Domain-Knowledge.git
cd Constrained-Deep-Clustering-of-scRNA-seq-Data-with-Limited-Domain-Knowledge
```

### Setup environment
```bash
conda create -n scdcc python=3.11 -y
conda activate scdcc
pip install -r requirements.txt
```

### Key Dependencies
```bash
pip install -r requirements.txt
```

---

## ▶️ Usage

### Step 1: Preprocess datasets
Run the dataset-specific notebooks:  
```bash
preprocessing_mouse_bladder.ipynb
preprocessing_pbmc4k.ipynb
preprocessing_worm_neuron.ipynb
preprocessing_human_pancreas.ipynb
```
This generates `.h5ad` files in `processed_dataset/`.

### Step 2: Train & evaluate models
Run **`algorithm.ipynb`** to execute K-means, DEC, and scDCC.  
Results are automatically saved in the `results/{dataset_name}/` folder.

### Step 3: View results
- **Bar plots**: Compare performance of K-means, DEC, and scDCC.  
- **Constraint curves**: Performance vs number of pairwise constraints.  
- **UMAPs**: Cluster visualization compared with ground truth.  

### Step 4: Presentation
`Presentation.ipynb` contains visual slides summarizing findings.

---

## 📊 Results

### scDCC Performance Across Datasets

| **Dataset**             | **NMI (Test)** | **ARI (Test)** | **CA (Test)** |
|--------------------------|----------------|----------------|---------------|
| **Baron Human Pancreas** | 0.910          | 0.933          | 0.973         |
| **Mouse Bladder**        | 0.769          | 0.738          | 0.828         |
| **PBMC 4k**              | 0.967          | 0.991          | 0.989         |
| **Worm Neuron**          | 0.887          | 0.855          | 0.938         |

scDCC consistently outperforms baseline methods (K-means, DEC) across all datasets, particularly excelling in complex datasets like PBMC and Worm Neuron.  

See the `results/` folder for comparative plots and UMAP visualizations.

---

## 📧 Contact
**Author:** Kashif Moin  
- GitHub: [KashifMoin1410](https://github.com/KashifMoin1410)  
- University of Manchester, MSc Advanced Computer Science (AI)  
