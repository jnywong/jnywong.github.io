---
title: "slurpy"
author: Jenny Wong
---

[![GitHub Badge](https://img.shields.io/badge/GitHub-slurpy-purple?logo=github)](https:github.com/jnywong/nondim-slurry)
[![PyPI version](https://badge.fury.io/py/nondim-slurry.svg)](https://badge.fury.io/py/nondim-slurry)
[![Build Status](https://travis-ci.org/jnywong/nondim-slurry.svg?branch=master)](https://travis-ci.org/jnywong/nondim-slurry)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4446750.svg)](https://doi.org/10.5281/zenodo.4446750)

An open source python package to solve the 1D, steady, spherical slurry system outlined in [Wong et al. (2021)](https://www.sciencedirect.com/science/article/am/pii/S0012821X21000509) (see also [Wong et al. 2018](https://academic.oup.com/gji/article-pdf/214/3/2236/36134435/ggy245.pdf)).

## Getting Started

### Prerequisites
- [Python](https://www.python.org/)

### Installing
Conda:
```
conda install -c jnywong nondim-slurry
```

Pip:
```
pip install nondim-slurry
```

Git:

Find the latest version of the repository [here](https://github.com/jnywong/nondim-slurry).

## Package structure
```
slurpy/
  __init__.py
  coreproperties.py
  data_utils.py
  getparameters.py
  lookup.py
  lookupdata/
    denPREM.csv
    gravPREM.csv
    presPREM.csv
    radAK135.csv
    radPREM.csv
    vpAK135.csv
    vpPREM.csv
  plot_utils.py
  scripts/
    parameter_search.py
    seismic.py
    sensitivity.py
  slurry.py
```

## Example scripts

### Parameter search

1. Open `scripts/parameter_search.py`

2. Enter some input parameters. For example, try:

```
# %% MODEL INPUTS
# Show plots?
plotOn=1 # show temp, xi, solid flux and density profiles

# Input parameters
layer_thicknesses=np.array([150e3]) # (m)
thermal_conductivities=np.array([100.]) # (W m^-1 K^-1)
icb_heatfluxes=np.array([3.4]) # (TW)
csb_heatfluxes=np.array([7.4]) # (TW)

h=0.05 # stepsize of heat flux through parameter space
```

3. Run `parameter_search.py`

4. Admire the output:

![](https://github.com/jnywong/nondim-slurry/blob/master/docs/simple_output.png?raw=true)

### Sensitivity study

1. Open `scripts/sensitivity.py`

2. Enter some input parameters. For example, try:

```
# %% MODEL INPUTS
# Save plot?
saveOn=0

# Input parameters
layer_thickness=150e3 # (m)
thermal_conductivity=100. # (W m^-1 K^-1)
icb_heatflux=2.5 # (TW)
csb_heatflux=5.0 # (TW)
h=0.05 # stepsize of heat flux through parameter space

# Sensitivity study
csb_temp = np.arange(4500.,6100.,100) # (K)
csb_oxy = np.arange(2,12.5,0.5) # (mol.%)
sed_con= np.array([1e-5,1e-4,1e-3,1e-2,1e-1]) # (kg s/m^3) pre-factor in sedimentation coefficient, b(phi)
```

3. Run `sensitivity.py`

4. Admire the output:

![](https://github.com/jnywong/nondim-slurry/blob/master/docs/sensitivity_example.png?raw=true)

## Links
* [PyPI](https://pypi.org/project/nondim-slurry/)
* [Anaconda Cloud](https://anaconda.org/jnywong/nondim-slurry)

## Authors

* [**Jenny Wong**](https://jnywong.github.io/) - *University of Leeds - Institut de Physique du Globe de Paris - Institut des Sciences de la Terre*
* [**Chris Davies**](https://environment.leeds.ac.uk/see/staff/1225/dr-chris-davies) - *University of Leeds*
* [**Chris Jones**](https://eps.leeds.ac.uk/maths/staff/4042/professor-christopher-jones-) - *University of Leeds*

## License

This project is licensed under the MIT License - see the [LICENSE.md](https://github.com/jnywong/nondim-slurry/blob/master/LICENSE.md) file for details

## Acknowledgments

* ERC SEIC
* Del Duca Foundation
* EPSRC Centre for Doctoral Training in Fluid Dynamics

🎉
