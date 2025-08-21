# Polymer-Penalty

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Code and derived parameters for the manuscript: **Polymer-derived distance penalties improve chromatin interaction predictions from single-cell data across crop genomes**.

This repository provides a framework to correct the systematic distance bias found in proxy data of 3D genome architecture, such as single-cell co-accessibility scores (scATAC-seq) or Deep Learning predictions. 
The method is grounded in polymer physics and uses experimental Hi-C data to derive a species-specific penalty function.

---

## Workflow

The method takes biased proxy data (e.g., co-accessibility scores) and a reference Hi-C dataset as input. 
It fits a multi-component power-law model to the Hi-C data to derive a penalty function, which is then applied to the proxy scores to produce a corrected, physically realistic interaction map.


![Workflow Schematic](https://github.com/user-attachments/assets/8ac39991-2314-4140-a223-7416ccf280f8)

---

--

## Installation

To get started, clone the repository and install the required Python packages.

### 1. Clone the repository
```bash
git clone https://github.com/jlab-code/polymer-penalty.git
```

### 2. Navigate into the directory
```bash
cd polymer-penalty
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

---

## Usage

This framework has two main workflows:
1. Deriving a new, custom penalty function from your own Hi-C data
2. Applying a pre-computed penalty function to correct your proxy data (e.g., co-accessibility scores)

---

### Workflow 1: Deriving a Custom Penalty Function

To generate a penalty function for a new species or cell type, you will need a file of chromatin loops from Hi-C data.

1. Place your Hi-C loop file (in `.bedpe` format) in the `data/` directory.
2. Open and run the Jupyter Notebook: `scripts/get_penalty_function.ipynb`.
3. In the notebook, find the cell that defines the input file path and change it to your file:
   ```python
   # Before
   hic_path = "../data/soybean_leaf_HiC.hiccups_loops.fdr0.1.bedpe"

   # After
   hic_path = "../data/your_hic_data.bedpe"
   ```
4. Run all the cells in the notebook.
5. The script will output a new file containing your custom parameters, e.g. `penalty_functions/your_species_penalty_parameters.tsv`.

---

### Workflow 2: Applying a Penalty Function

Once you have a penalty function (either one we provided or one you derived), you can use it to correct your co-accessibility or Deep Learning scores.

1. Place your co-accessibility file (in `.csv` or `.tsv` format) in the `data/` directory.
2. Open and run the Jupyter Notebook: scripts/apply_penalty.ipynb.
3. In the first code cell, update the SPECIES_TO_RUN variable and ensure the file paths are correct for your data.
   ```python
   # USER: Select wich species to run
   SPECIES_TO_RUN = "Soybean" # Options: "Maize", "Soybean", "Rice", or your custom name
   
   # --- Update file paths for your custom data ---
   coacr_file = os.path.join(data_directory, "your_coaccessibility_scores.csv")
   penalty_file = os.path.join(penalty_directory, "your_species_penalty_parameters.tsv")
   ```
4. Run all the cells in the notebook.
5. The script will generate a new file with the corrected scores in the `results/` directory.

A test run using the provided example data for soybean is configured by default in the notebooks.
