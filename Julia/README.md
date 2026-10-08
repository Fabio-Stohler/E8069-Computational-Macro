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
downloads and compiles Plots, IJulia and DataInterpolations, which takes a few minutes.

Tell VS Code to use this environment as well: click on the environment
name in the bottom status bar (it says `Julia env: ...`) and pick this
folder, or run "Julia: Change Current Environment" from the command
palette (`Ctrl+Shift+P`). From then on, the REPL that VS Code starts for
you has the packages available.

## Updating the environment after a pull

When a week adds a package (week 3 adds `DataInterpolations`, week 5 adds `QuantEcon`), the files
`Project.toml` and `Manifest.toml` in this folder change when you pull, but
the package is not on your laptop yet. You do not need to do anything: the
first code cell of the notebooks from week 5 on activates the course environment and
runs `Pkg.instantiate()`, which installs whatever is missing. The first run after
such a pull downloads and compiles the new package and can take a few minutes.

Only if that cell fails, install the packages by hand, as follows:

1. **Pull the course repository.** In GitHub Desktop: select the course
   repository, click "Fetch origin" and then "Pull origin". Or, in a terminal
   in the repository folder, run `git pull`.
2. **Open a terminal in VS Code.** Open the repository folder in VS Code (File,
   Open Folder), then open a terminal with Terminal, New Terminal (or
   ``Ctrl+` ``). The terminal starts in the repository folder, the one that
   contains `Julia/` and `Python/`.
3. **Move to the Julia folder.** Type

   ```
   cd Julia
   ```

   and press Enter. This works in PowerShell (Windows) and in the terminal on
   macOS and Linux. Check with `ls`: you should see `Project.toml` and
   `Manifest.toml`.
4. **Start Julia** in this folder by typing `julia` and pressing Enter. The
   prompt changes to `julia>`.
5. **Update the packages.** Press `]` to enter the package mode, the prompt
   changes to `(@v1.10) pkg>` (or your Julia version). Then run

   ```
   activate .
   instantiate
   ```

   `activate .` selects the course environment in this folder (the prompt now
   reads `(Julia) pkg>`), `instantiate` installs every package listed in
   `Manifest.toml` that is missing on your laptop. This downloads and compiles
   the new packages and can take a few minutes.
6. **Check.** Press backspace to leave the package mode, then type
   `using DataInterpolations`. If no error appears, you are done. Leave Julia
   with `exit()`.
7. **Restart the notebook kernel** if a notebook was open in VS Code while you
   did this (the restart button at the top of the notebook), so that it sees the
   new package.

If you started Julia somewhere else, you do not need to quit: in Julia, type
`cd("path/to/the/repository/Julia")` (with your path, forward slashes also work
on Windows), check with `pwd()`, and continue with step 5.

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

## Week 3: value function iteration off the grid

**In class.** `Week_3/vfi_off_grid.ipynb` continues with the growth model of
week 2, but the household may now choose capital between the grid points.
Part 1 zooms in on last week's policy, part 2 builds linear interpolation,
takes the natural cubic spline from the package `DataInterpolations` and checks
what the spline promises at the nodes (it goes through the points, its first and
second derivative are continuous), part 3 is golden section search, part 4 puts
the two together in the Bellman step. Part 5, Howard's improvement algorithm,
and the experiments of part 6 are for home. Gaps are marked `___`, the comment
next to each one says what goes in, and every part ends with a small test or a
number to compare. `Week_3/vfi_off_grid_solution.ipynb` is posted after the
session.

**New package.** Week 3 adds `DataInterpolations` to the environment. Update
the environment before class, see "Updating the environment after a pull"
above.

**AI-assisted coding.** `Week_3/ai_prompts.md` has the three prompts of the
exercise in class, the questions to discuss, the course policy in short, and
links to free courses on working with AI assistants.

## Week 5: Markov chains with QuantEcon, time iteration, and the endogenous grid method

**In class (Thursday, 08.10.2026).** `Week_5/markov_chains_and_egm.ipynb` has three parts.
Part 1 puts income on a grid with `tauchen` and `rouwenhorst` from the
`QuantEcon` package, prints and compares the transition matrices, computes the
stationary distribution and the moments of each chain for several persistences,
and simulates a path, by hand and with `simulate_indices`. Parts 2 and 3 solve
the CARA household of the session 5 slides with time iteration (expected
marginal utility as a matrix product, the Euler residual, vectorized bisection)
and with the endogenous grid method, and measure both against the exact policy.
Gaps are marked `___`, the comment next
to each one says what goes in, and every part ends with a number to compare.
`Week_5/markov_chains_and_egm_solution.ipynb` is posted after the session.

**New package.** Week 5 adds `QuantEcon` to the environment. Pull before class
and run the first cell of the notebook, which installs it (a few minutes the
first time), or follow "Updating the environment after a pull" above.
