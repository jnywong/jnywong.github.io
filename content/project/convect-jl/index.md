---
title: convect-jl
summary: An open source Julia code to simulate 2D convection in a Cartesian box. 
tags:
  - research
date: "2021-08-08T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: 
  focal_point: Smart
  preview_only: true
  alt_text: 2D contour plot of velocity field in a non-linear convecting system

links:
- icon: github
  icon_pack: fab
  name: GitHub
  url: https://github.com/jnywong/convect-jl
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

<p align="center">
  <img src="https://raw.githubusercontent.com/jnywong/convect-jl/main/docs/figures/video.gif" />
</p>

Welcome! Here is my Julia code to simulate 2D convection in a Cartesian box. Theory and methods used can be found in [Introduction to Modeling Convection in Planets and Stars: Magnetic Field, Density Stratification, Rotation](https://press.princeton.edu/books/hardcover/9780691141725/introduction-to-modeling-convection-in-planets-and-stars). 

## Getting Started

### Pre-requisites
- [Julia](https://julialang.org/) (version 1.6)

## Package structure
```
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
   
```
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

![](docs/figures/linear.png)

### Nonlinear convection

1. Open `src/convect_nonlinear.jl`

2. Specify input parameters
   
```
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

```
# Inputs
saveDir = "/Users/wongj/Documents/convect-out/2021-09-03" # save directory
nStart = 1
nEnd = 500
zeroth= 1 # plot zeroth mode?
```

5. Admire the output:

![](https://raw.githubusercontent.com/jnywong/convect-jl/main/docs/figures/video.gif)

## Authors

* [**Jenny Wong**](https://jnywong.github.io/) - *Institut des Sciences de la Terre*
  

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

:tada: