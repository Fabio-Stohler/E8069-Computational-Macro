# Julia material

Code for the Julia track of the course. Each week has its own folder. The
Python track lives in `../Python` and covers the same content, pick one
language and stick with it.

## Setup

This folder is a Julia environment: `Project.toml` lists the packages we
use and `Manifest.toml` pins their exact versions, so that everybody in
class runs the same code. Install the packages once. Start Julia in this
folder (in VS Code: right click the `Julia` folder, "Open in Integrated
Terminal", then type `julia`), press `]` to enter the package mode and
run

```
activate .
instantiate
```

Press backspace to leave the package mode. The first `instantiate`
downloads and compiles Plots and IJulia, which takes a few minutes.

Tell VS Code to use this environment as well: click on the environment
name in the bottom status bar (it says `Julia env: ...`) and pick this
folder, or run "Julia: Change Current Environment" from the command
palette (`Ctrl+Shift+P`). From then on, the REPL that VS Code starts for
you has the packages available.

## How to run the notebooks

All material comes as Jupyter notebooks (`.ipynb`). The Julia kernel for
Jupyter is the package IJulia, which is part of the course environment
and gets installed by `instantiate` above. Run once, in the Julia REPL
with the environment active,

```
using IJulia
```

so that the kernel registers itself with Jupyter. Then open the notebook
in VS Code (the Julia and Jupyter extensions must be installed), pick the
Julia kernel in the top right corner when asked, and run the cells from
top to bottom with `Shift+Enter`. Read the output of each cell, and
change things to see what happens. Plots appear below the cell that
draws them.

If VS Code does not offer a Julia kernel, run `using IJulia; notebook()`
in the REPL instead, which opens the classic Jupyter interface in the
browser (it offers to install a private Jupyter the first time).

Two things that surprise newcomers: Julia indexes from 1, and the first
call of a function (and the first plot) is slow because Julia compiles it.
The second call is fast.

## Week 1: primer

Read before the next session. `Week_1/Week_1_revision.ipynb` introduces the
language constructs that the live coding in class uses, and nothing else, with the
growth model of session 1 as the running example (log utility, production
`k^α`, full depreciation, `α = 0.3` and `β = 0.96` as on the slides). It starts with how to select the course
environment in VS Code (see the setup section above). Five short parts, three
exercises at the end.

| Part | Language | Session 1 material |
| --- | --- | --- |
| 1. Arrays | `range`, `collect`, the dot for elementwise operations, `exp.` and `log.` | the capital grid, output `k^α`, the policy `αβ k^α`, an equidistant and a log spaced grid |
| 2. Containers | `Base.@kwdef` structs with keyword construction, named tuples | `par`, `mpar`, `gri` |
| 3. Functions | the short form `f(x) = ...`, the long form `function ... end`, applying a function to a vector with a dot | the utility function, the closed form value function `E + F ln k` and policy `αβ k^α`, evaluated on the grid |
| 4. Loops | `while` with a condition, here a tolerance and an iteration cap, `global`, `push!`, a `for` loop, `@printf` | the recursion `F_{n+1} = α + αβ F_n` run to its limit, the contraction factor `αβ` read off the distances |
| 5. Plots | `plot`, `plot!`, `scatter!`, `yaxis = :log10`, `hline!`, `layout` | the closed form value and policy functions with the steady state, the convergence of the recursion |

## Week 2: value function iteration on a grid

**In class.** `Week_2/vfi_on_grid.ipynb` is the notebook we fill in together in
session 2: the deterministic growth model of session 1, solved by value
function iteration on a grid, in the structure used by all later templates
(one container for the economic parameters, one for the numerical ones,
the grid, the meshes, the utility function, the loop with a timer, the
checks against the closed form). Gaps are marked `___`, each one is one line
of the pseudo-code on the slides. Section 6 holds the grid experiments, with
an empty cell to try them in. `Week_2/vfi_on_grid_solution.ipynb` is posted
after the session.
