# ENZO-BRASIL
# Monte Carlo simulation framework for a spatial Bayesian Hierachical Bimodal Generalized Extreme Value model with Gaussian Process priors implemented in Stan.

This repository implements a full Monte Carlo simulation framework for a spatial Bayesian BGEV models with Gaussian Process structure in the location parameter.

The project was developed to investigate parameter recovery, posterior diagnostics, and computational stability under varying spatial sample sizes and tail configurations under complex scenarios of extreme values, such as bimodality.

---
## Model Overview

We consider a spatial BGEV model of the form:

- Site-specific location parameter:
  
  μ_s = X_s β + f_s

- f_s follows a Gaussian Process with exponential covariance kernel.

Inference is performed using Hamiltonian Monte Carlo via Stan.

---

## Key Features

- Deterministic simulation design
- Monte Carlo grid exploration over:
  - Number of sites (S)
  - Replicates per site (T)
  - Tail parameter ξ
  - Shape deformation parameter δ
- Automatic diagnostic extraction:
  - R̂
  - Effective sample size
  - Divergences
  - Treedepth
- Atomic checkpointing system
- Recovery analysis with 95% CI coverage

---

## Structure

- `src/stan/` — Stan model
- `src/simulation/` — Data-generating process
- `src/inference/` — Estimation and diagnostics
- `scripts/` — Main execution script
- `results/` — Output summaries

---

## Reproducibility

All simulations use deterministic seeds.

To reproduce results:

```r
source("scripts/run_simulation_grid.R")
