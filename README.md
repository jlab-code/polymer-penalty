# Polymer-Penalty

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Code and derived parameters for the manuscript: **Polymer-derived distance penalties improve chromatin interaction predictions from single-cell data across crop genomes**.

This repository provides a framework to correct the systematic distance bias found in proxy data of 3D genome architecture, such as single-cell co-accessibility scores (scATAC-seq) or Deep Learning predictions. 
The method is grounded in polymer physics and uses experimental Hi-C data to derive a species-specific penalty function.

---

## Workflow

The method takes biased proxy data (e.g., co-accessibility scores) and a reference Hi-C dataset as input. 
It fits a multi-component power-law model to the Hi-C data to derive a penalty function, which is then applied to the proxy scores to produce a corrected, physically realistic interaction map.




---

## Installation

To get started, clone the repository and install the required Python packages.

```bash
# 1. Clone the repository
git clone [https://github.com/jlab-code/polymer-penalty.git](https://github.com/jlab-code/polymer-penalty.git)

# 2. Navigate into the directory
cd polymer-penalty

# 3. Install dependencies
pip install -r requirements.txt
