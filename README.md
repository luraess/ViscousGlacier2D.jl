# ViscousGlacier2D
Concise and CPU and GPU iterative Stokes solvers for viscous flow - 2D glacier examples.


## Description
This repository contains GPU and CPU implementations of a 2D Stokes solver to resolve glacier flow on an inclined plane with a stress-free surface. The routines exemplify the implementation of a fast and concise (60 lines of code) iterative solving strategy referred to as Pseudo-Transient. The core of the Pseudo-Transient approach relies in using physics-motivated transient terms within differential equations in order to iteratively converge to an accurate solution.

The routines relate to a seminar on _"Simply solving PDEs"_. The seminar presentation is accessible [here](#seminar-presentation). Further material relating to the pseudo-transient method and pseudo-transient solvers can be found [here](https://ptsolvers.github.io).


## Content
* [Script list](#script-list)
* [Usage](#usage)
* [Output](#output)
* [Questions and comments](#questions-and-comments)
* [Seminar presentation](#seminar-presentation)


## Script list
The [/scripts](/scripts/) folder contains the following PT routines:
- [`viscous_gl2D.jl`](scripts/viscous_gl2D.jl)
- [`viscous_gl2D_gpu.jl`](scripts/viscous_gl2D_gpu.jl)
- [`viscous_gl2D_nondim.jl`](scripts/viscous_gl2D_nondim.jl)
- [`viscous_gl2D_nondim_gpu.jl`](scripts/viscous_gl2D_nondim_gpu.jl)

The keywords in the code naming stand for:
- gpu: Nvidia GPU ready routines using the [CUDA.jl] package
- nondim: non-dimensional version of the code, using natural scaling


## Usage
The routines are written in [Julia] and can be executed from the REPL. Output is produced using [PyPlot.jl] requiring a valid and on `PATH` python (+ matplotlib) install.

Example running the `viscous_gl2D_nondim.jl` routine.

1. Launch Julia
```sh
% julia --project
```
2. ENter package mode `]` and instantiate the environment
```julia-repl
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.5.0 (2020-08-01)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

julia>

(ViscousGlacier2D) pkg> add instantiate

(ViscousGlacier2D) pkg> st
Status `~/Documents/git/github/ViscousGlacier2D/Project.toml`
  [d330b81b] PyPlot v2.9.0

(ViscousGlacier2D) pkg> 

julia> 
```
3. Run the script
```julia-repl
julia> include("scripts/viscous_gl2D_nondim.jl")
error = 0.007844763087162187
error = 0.0035814871757943543
error = 0.0005235773871451197
error = 6.932325914314143e-5
error = 2.3742721434622532e-5
error = 9.103473750402527e-7
error = 7.903400522027475e-7
error = 7.196251086591826e-8
error = 1.9440634300592754e-8
error = 4.161439365592243e-9
error = 2.54854535939787e-10
error = 1.6094254786093418e-10

julia> 
```

## Output
The output of running the `viscous_gl2D_nondim.jl` script is following
![Viscous 2D full Stokes flow (2D glacier) with stress free surface](docs/fig_viscous_gl2D_nondim.png)

## Questions and comments
Contact me or open an [issue](https://github.com/luraess/ViscousGlacier2D.jl/issues) if you have any questions or comments about the presented material.

## Seminar presentation

![Simply solving PDEs](docs/slides.png)


[Julia]: https://julialang.org
[CUDA.jl]: https://github.com/JuliaGPU/CUDA.jl
[PyPlot.jl]: https://github.com/JuliaPy/PyPlot.jl
