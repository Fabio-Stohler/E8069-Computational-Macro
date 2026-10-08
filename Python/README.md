# Python material

Code for the Python track of the course. Each week has its own folder. The
Julia track lives in `../Julia` and covers the same content, pick one
language and stick with it.

## Setup

Create the course environment once. It pins the package versions so that
everybody in class runs the same code. In a terminal (Windows: Anaconda
Prompt), from this folder:

```
conda env create -f environment.yml
conda activate compmacro
```

Then tell VS Code to use it: open any `.py` file, run "Python: Select
Interpreter" from the command palette (`Ctrl+Shift+P`) and pick
`compmacro`.

If you prefer `pip` and virtual environments, the packages we need this
week are only `numpy` and `matplotlib` (plus `ipykernel` for running cells
in VS Code):

```
python -m venv .venv
.venv\Scripts\activate          (Windows)
source .venv/bin/activate       (macOS, Linux)
pip install numpy matplotlib ipykernel
```

## How to run the notebooks

All material comes as Jupyter notebooks (`.ipynb`). Open the notebook in
VS Code (the Python and Jupyter extensions must be installed), pick the
`compmacro` kernel in the top right corner when asked, and run the cells
from top to bottom with `Shift+Enter`. Read the output of each cell, and
change things to see what happens. Plots appear below the cell that
draws them.

If you prefer the classic interface, `jupyter lab` in a terminal with the
environment activated opens the notebooks in the browser.

## Week 1: primer

Read before the next session. `Week_1/Week_1_revision.ipynb` introduces the
language constructs that the live coding in class uses, and nothing else, with the
growth model of session 1 as the running example (log utility, production
`k^alpha`, full depreciation, `alpha = 0.3` and `beta = 0.96` as on the slides). It starts with how to select the course
environment in VS Code (see the setup section above). Five short parts, three
exercises at the end.

| Part | Language | Session 1 material |
| --- | --- | --- |
| 1. Arrays | `np.linspace`, elementwise arithmetic on arrays, `np.exp` and `np.log` | the capital grid, output `k^alpha`, the policy `alpha beta k^alpha`, an equidistant and a log spaced grid |
| 2. Containers | frozen dataclasses with keyword construction | `par`, `mpar`, `gri` |
| 3. Functions | `def` with a body and `return`, the `lambda` form, applying a function to an array | the utility function, the closed form value function `E + F ln k` and policy `alpha beta k^alpha`, evaluated on the grid |
| 4. Loops | `while` with a condition, here a tolerance and an iteration cap, lists and `append`, a `for` loop, f-strings | the recursion `F_{n+1} = alpha + alpha beta F_n` run to its limit, the contraction factor `alpha beta` read off the distances |
| 5. Plots | `plt.subplots`, `plot`, `scatter`, `semilogy`, `axhline`, `legend` | the closed form value and policy functions with the steady state, the convergence of the recursion |

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
takes the natural cubic spline from `scipy.interpolate.CubicSpline` and checks
what the spline promises at the nodes (it goes through the points, its first and
second derivative are continuous), part 3 is golden section search, part 4 puts
the two together in the Bellman step. Part 5, Howard's improvement algorithm,
and the experiments of part 6 are for home. Gaps are marked `___`, the comment
next to each one says what goes in, and every part ends with a small test or a
number to compare. `scipy` is part of the `compmacro` environment already.
If it is missing on your laptop, run `conda install -n compmacro scipy` in a terminal (or `pip install scipy` if you installed without conda). `Week_3/vfi_off_grid_solution.ipynb` is posted
after the session.

**AI-assisted coding.** `Week_3/ai_prompts.md` has the three prompts of the
exercise in class, the questions to discuss, the course policy in short, and
links to free courses on working with AI assistants.

## Week 5: Markov chains with QuantEcon, time iteration, and the endogenous grid method

**In class (Thursday, 08.10.2026).** `Week_5/markov_chains_and_egm.ipynb` has three parts.
Part 1 puts income on a grid with `qe.tauchen` and `qe.rouwenhorst` from the
`quantecon` package, prints and compares the transition matrices, computes the
stationary distribution and the moments of each chain for several persistences,
and simulates a path, by hand and with `MarkovChain.simulate_indices`. Parts 2
and 3 solve the CARA household of the session 5 slides with time iteration
(expected marginal utility as a matrix product, the Euler residual, vectorized
bisection) and with the endogenous grid method, and measure both against the
exact policy. Gaps are marked `___`,
the comment next to each one says what goes in, and every part ends with a
number to compare. `Week_5/markov_chains_and_egm_solution.ipynb` is posted
after the session.

**New package.** Week 5 adds `quantecon` to the environment. Either update the
environment with `conda env update -f environment.yml` from this folder, or
let the first cell of the notebook install it into the running kernel.
