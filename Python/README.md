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

Read before the next session. `Week_1/Week_1_primer.ipynb` introduces the
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
