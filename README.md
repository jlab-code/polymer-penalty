# Polymer-Penalty

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Code and derived parameters for the manuscript: **Polymer-derived distance penalties improve chromatin interaction predictions from single-cell data across crop genomes**.

This repository provides a framework to correct the systematic distance bias found in proxy data of 3D genome architecture.

---

## Workflow

The method takes biased proxy data and a reference Hi-C dataset as input. It fits a multi-component power-law model to the Hi-C data to derive a penalty function.

---

## Installation

### 1. Clone the repository
```bash
git clone [https://github.com/jlab-code/polymer-penalty.git](https://github.com/jlab-code/polymer-penalty.git)
cd polymer-penalty
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

---

## Usage

### Workflow 1: Applying Pre-computed Global Consensus Penalties
Use our parameters derived for **Soybean, Rice, and Maize**.

1. Place your co-accessibility scores in the `data/` directory.
2. Open the Jupyter Notebook: `scripts/apply_correction.ipynb`.
3. Select your target species:
```python
# USER: Select species and model type
SPECIES = "Soybean"          
USE_GLOBAL_CONSENSUS = True  
```
4. Run all cells. 

---

### Workflow 2: Deriving Custom Penalties for New Species
Use our GMM-pipeline to generate a custom model for any species.

1. Place your Hi-C loops in `.bedpe` format in the `data/` directory.
2. Open the Jupyter Notebook: `scripts/get_penalty_function.ipynb`.
3. Update the data path:
```python
hic_path = "../data/your_new_species_HiC.bedpe"
```
4. Run all cells. 

---

## Key Features
* **Neutral Zone Protection:** Distances below **35 kb** are preserved (penalty = 1.0).
* **High-Precision PKL:** Utilizes floating-point accurate power-law exponents and transition points.
* **Multi-Regime Modeling:** Captures complex folding (S1, S2, S3) in crop genomes.

---

## Citation
> *Polymer-derived distance penalties improve chromatin interaction predictions from single-cell data across crop genomes.* (2026).

---