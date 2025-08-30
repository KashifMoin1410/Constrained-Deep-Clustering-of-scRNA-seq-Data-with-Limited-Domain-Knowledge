# Constrained Deep Clustering of scRNA-seq Data with Limited Domain Knowledge

## About the Project
This project focuses on clustering single-cell RNA sequencing (scRNA-seq) data using both traditional and deep learning approaches. We implement three clustering methods:
- **K-means** (unsupervised baseline),
- **Deep Embedded Clustering (DEC)**,
- **Single-cell Deep Constrained Clustering (scDCC)**.

The main objective is to evaluate how integrating limited domain knowledge through pairwise constraints (must-link and cannot-link) can enhance clustering accuracy, biological interpretability, and robustness. Experiments were conducted across four benchmark datasets: Mouse Bladder, Worm Neuron, PBMC 4k, and Baron Human Pancreas.

## Built With
- [Python](https://www.python.org/)
- [Jupyter](https://jupyter.org/)
- [PyTorch](https://pytorch.org/)
- [Scanpy](https://scanpy.readthedocs.io/)
- [Scikit-learn](https://scikit-learn.org/)

## Getting Started

To get a local copy up and running, follow these steps:

### Prerequisites
- Python 3.10 or higher
- pip (Python package manager)
- conda (optional, recommended for reproducibility)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/KashifMoin1410/Constrained-Deep-Clustering-of-scRNA-seq-Data-with-Limited-Domain-Knowledge.git
cd Constrained-Deep-Clustering-of-scRNA-seq-Data-with-Limited-Domain-Knowledge
```

2. (Optional) Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

## Datasets
The following publicly available scRNA-seq datasets were used in this study:

- **Baron Human Pancreas**: [GEO Accession GSE84133](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE84133)  
- **Mouse Bladder & Worm Neuron**: [scDCC Figshare Repository](https://figshare.com/articles/dataset/scDCC_data/21563517?file=38224590)  
- **PBMC 4k (10x Genomics)**: [PBMC 4k Dataset](https://www.10xgenomics.com/datasets/4-k-pbm-cs-from-a-healthy-donor-2-standard-2-1-0)  

## Project Structure
- **requirements.txt** – Python dependencies for running all experiments.  
- **/notebooks/** – Jupyter notebooks for preprocessing, training, and evaluation.  
- **/models/** – Implementations of K-means, DEC, and scDCC (PyTorch).  
- **/results/** – Figures, plots, and metrics from clustering experiments.  
- **/datasets/** – Scripts for downloading and preprocessing benchmark datasets.  
- **/visualizations/** – UMAP and constraint-performance plots used in the dissertation.  

## Reproducibility
To ensure consistent results, the following practices were applied:
- Fixed random seeds (`numpy`, `torch`, and `scikit-learn`) for repeatable runs.  
- Dataset splits into training/validation/test were stratified and seeded.  
- Each experiment was run **10 times with different seeds**, and mean performance reported.  
- GPU acceleration (NVIDIA Tesla T4, CUDA 12.4) was used, but CPU runs are also supported (with longer runtimes).  

To reproduce results from the dissertation:
1. Preprocess datasets using the scripts in `/datasets/`.  
2. Run model training and evaluation via the notebooks in `/notebooks/`.  
3. Generated plots and metrics will be saved automatically in `/results/`.  

## Contact
- **Kashif Moin**  
  GitHub: [KashifMoin1410](https://github.com/KashifMoin1410)  

## Other Remarks
The dissertation accompanying this repository discusses:
- The methodology behind K-means, DEC, and scDCC,  
- How pairwise constraints improve clustering performance,  
- Comparative evaluation across datasets (NMI, ARI, CA),  
- Limitations and future directions for constrained deep clustering.  
