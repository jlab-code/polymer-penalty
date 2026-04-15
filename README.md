# Polymer-Penalty

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![DOI](https://img.shields.io/badge/Zenodo-Data-blue.svg)](https://doi.org/10.5281/zenodo.18607660)

Code and derived parameters for the manuscript: **A multi-component power-law penalty corrects distance bias in single-cell co-accessibility and deep-learning chromatin interaction predictions**.

---

## Data Availability
The processed datasets, including Hi-C loop sets and co-accessibility scores used in this study, are available on Zenodo:  
👉 **[Link to Zenodo Dataset](https://doi.org/10.5281/zenodo.18607660)**

---

## Installation

### 1. Clone the repository
```bash
git clone https://github.com/jlab-code/polymer-penalty.git
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
---
## Repository Note
The code in this repository is actively maintained. For the latest features, bug fixes, and parameter updates, please refer to the **GitHub repository**: [https://github.com/jlab-code/polymer-penalty](https://github.com/jlab-code/polymer-penalty).


## Citation
> *A multi-component power-law penalty corrects distance bias in single-cell co-accessibility and deep-learning chromatin interaction predictions.* (2026).

---