# Inference in Tumour–Immunotherapy Dynamics — Research Code

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)

This repository contains the full, reproducible codebase that accompanies the
paper

> **Inference in Tumour–Immunotherapy Dynamics**  
> *Yazan Ghafir & Nikos Kavallaris* (2025)

It implements data preprocessing, stochastic‐differential‐equation (SDE)
modelling, maximum‐likelihood and Bayesian parameter inference, Extended
Kalman / Particle filtering, and all statistical analyses reported in the
manuscript.

---

## Quick start (Colab)

> **One-click replication:**  
> Open the interactive Colab notebook below — no local setup required.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1A0m5bNgqdj6tUyX3XLM_R93lVuTB0xK9/view?usp=sharing)

The notebook:

1.  Downloads the **MU–Glioma–Post** cohort from TCIA.  
2.  Extracts volumetric tumour time-series for the 59 patients selected in the
    study.
3.  Reproduces every figure and table in a single run (≈ 15 min on Colab
    CPU).

---

## Repository structure

```
.
├── data/                  # Empty by default; dataset downloaded at runtime
├── notebooks/
│   └── tumour_sde.ipynb   # Main Colab / Jupyter notebook
├── src/
│   ├── io.py              # Data loading & mask processing
│   ├── models.py          # SDE drift & diffusion definitions
│   ├── inference.py       # MLE & PyMC-based Bayesian routines
│   ├── filters.py         # EKF & PF implementations
│   └── analyse.py         # Validation metrics & plotting helpers
├── figures/               # Auto-generated plots
├── environment.yml        # Conda spec (Python 3.11)
└── README.md
```

---

## Installation (local)

```bash
git clone https://github.com/<your-org>/tumour-immunotherapy-sde.git
cd tumour-immunotherapy-sde
conda env create -f environment.yml   # installs Python, numpy, scipy, pymc, etc.
conda activate tumour-sde
jupyter lab  # or run the notebook of your choice
```

> **Dataset note:**  
> The first run will download ≈ 3 GB of MRI data from TCIA
> (`data/` folder). You need ~10 GB free disk space for full processing.

---

## Reproducing the paper

| Step | Script / Notebook                         | Output                                |
|------|-------------------------------------------|---------------------------------------|
| 1    | `notebooks/tumour_sde.ipynb`              | Figures 2–7, parameter tables         |
| 2    | `python src/analyse.py --summary`         | `results/summary.csv` (AIC/BIC, RMSE) |
| 3    | `python src/analyse.py --patient 0006`    | Per-patient sensitivity plots         |

All derived artefacts are stored in `figures/` and `results/`.

---

## Citing

If you use this code or the accompanying dataset in your research, please cite
the paper (BibTeX entry in `CITATION.cff`) **and** acknowledge the data source:

```
@dataset{tcia_pkg_2022,
  title  = {PKG – Glioma Post},
  year   = {2022},
  note   = {The Cancer Imaging Archive},
}
```

---

## Contributing

Pull requests are welcome — especially for:

* Alternative SDE drift/diffusion formulations  
* Faster filtering schemes (parallel PF, Rao–Blackwellised PF)  
* Integration of clinical covariates (age, sex, IDH status, …)

Please open an issue to discuss major changes.

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE)
file for details.

---

### Contact

* **Yazan Ghafir** — <yazan.yasser.ghafir@gmail.com>  
* **Nikos Kavallaris** — <nikos.kavallaris@kau.se>

Feel free to reach out with questions, ideas, or collaborations!
