# SBMLToolkit

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://paulflang.github.io/SBMLToolkit.jl/stable)
[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://paulflang.github.io/SBMLToolkit.jl/dev)
[![Build Status](https://github.com/paulflang/SBMLToolkit.jl/workflows/CI/badge.svg)](https://github.com/paulflang/SBMLToolkit.jl/actions)
[![Coverage](https://codecov.io/gh/paulflang/SBMLToolkit.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/paulflang/SBMLToolkit.jl)

SBMLToolkit.jl is a lightweight tool to import models specified in the Systems Biology Markup Language (SBML) into the Julia SciML ecosystem. More specifically, SBMLToolkit.jl extracts reactions, initial conditions and parameter values from SBML files. Events, Rules and several other SBML components are not yet supported. There are multiple ways to specify the same model in SBML. Please help us improving SBMLToolkit.jl by creating a GitHub issue if you experience errors when converting your SBML model.

Note that [SBML.jl](https://github.com/LCSB-BioCore/SBML.jl) is a wrapper library of [libSBML](https://model.caltech.edu/software/libsbml/) and SBMLToolkit.jl is an extension for lowering these models into dynamical systems. 

## Installation
SBMLToolkit.jl is available on the Julia package managing system. To install SBMLToolkit run the following in the REPL:
  ```
  ]add SBMLToolkit
  ```

## Tutorial
SBML models can be simulated with the following steps:
  ```julia
    using SBMLToolkit

    rs = ReactionSystem("mymodel.sbml")
    odesys = convert(ODESystem, rs)

    tspan = [0., 1.]
    prob = ODEProblem(odesys, [], tspan, [])
    sol = solve(prob, Tsit5())
  ```

## License
The package is released under the [MIT license](https://github.com/paulflang/SBMLToolkit.jl/blob/main/LICENSE).


## Development team
This package was developed by [Paul F. Lang](https://www.linkedin.com/in/paul-lang-7b54a81a3/) at the University of Oxford, UK and [Anand Jain](https://github.com/anandijain) at the University of Chicago, USA.


## Questions and comments
Please contact [Paul F. Lang](mailto:paul.lang@wolfson.ox.ac.uk) or [Anand Jain](mailto:anandj@uchicago.edu) with any questions or comments.
