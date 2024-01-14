---
title: "convect-jl"
author: Jenny Wong
---

[![GitHub Badge](https://img.shields.io/badge/GitHub-convectjl-purple?logo=github)](https:github.com/jnywong/convect-jl)
[![](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Welcome! Here is my Julia code to simulate 2D convection in a Cartesian box. Theory and methods used can be found in [Introduction to Modeling Convection in Planets and Stars: Magnetic Field, Density Stratification, Rotation](https://press.princeton.edu/books/hardcover/9780691141725/introduction-to-modeling-convection-in-planets-and-stars).

## Getting Started

### Pre-requisites

- [Julia](https://julialang.org/) (version 1.6)

## Package structure

```shell
convect-jl
    docs/
    src/
        convect_linear.jl
        convect_nonlinear.jl
        critical_ra.jl
        data_utils.jl
        postprocess.jl
        routines.jl
    LICENSE.md
    README.md
```

## Examples

### Linear convection

1. Open `src/convect_linear.jl`

2. Specify input parameters

```julia
# Inputs
nz = 101 # no. of vertical gridpoints
nn = 30 # no. of horizontal Fourier modes (excluding zeroth mode)
a = 5 # L/D aspect ratio
Ra = 2700 # Rayleigh number
Pr = 0.5 # Prandtl number
nt = 1e5 # no. of timesteps
nout = 1e3 # output every nout timesteps
zeroth = 0 # include zeroth order temperature in plot?
initOn = 1
saveDir = "/Users/wongj/Documents/convect-out/linear/2021-09-03"
```

3. Run script from terminal using `julia <working directory>/convect-jl/src/convect_linear.jl` (or from julia REPL using `include("<working directory>/convect-jl/src/convect_linear.jl")` )

4. Admire the output:

![](https://github.com/jnywong/convect-jl/blob/main/docs/figures/linear.png?raw=true)

### Nonlinear convection

1. Open `src/convect_nonlinear.jl`

2. Specify input parameters
   
```julia
# Inputs
nz = 101 # no. of vertical gridpoints
nn = 50 # no. of Fourier modes (excluding zeroth mode)
a = 3 # L/D aspect ratio
Ra = 1e6 # Rayleigh number
Pr = 0.5 # Prandtl number
dt = 3e-6 # timestep size
nt = 1e4 # no. of timesteps
nout = 1e2 # save output every nout timesteps
initOn = 1 # initialise run, otherwise load existing data
saveDir = "/Users/wongj/Documents/convect-out/2021-09-03" # save directory
```

3. Run script from terminal using `julia <working directory>/convect-jl/src/convect_nonlinear.jl` (or from julia REPL using `include("<working directory>/convect-jl/src/convect_nonlinear.jl")` )

4. Postprocess and visualise the data using `julia <working directory>/convect-jl/src/postprocess.jl` (or from julia REPL using `include("<working directory>/convect-jl/src/postprocess.jl")` ) with the following input parameters

```julia
# Inputs
saveDir = "/Users/wongj/Documents/convect-out/2021-09-03" # save directory
nStart = 1
nEnd = 500
zeroth= 1 # plot zeroth mode?
```

5. Admire the output:

```{figure} ../media/gifs/convect-jl.gif
:alt: Simulation of non-linear convection in a 2D Cartesian box.
:width: 100%
:align: center
```

## Authors

* [**Jenny Wong**](https://jnywong.github.io/) - *Institut des Sciences de la Terre*

## License

This project is licensed under the MIT License - see the [LICENSE.md](https://github.com/jnywong/convect-jl/blob/main/LICENSE.md) file for details

🎉
