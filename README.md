# E8069 Computational Macro (HWS 2026)

Material for the PhD course Computational Macro at the University of Mannheim. The [syllabus](Syllabus.pdf) contains the course plan, assessment rules, literature, and trivia topics.

All coding content of the course (code templates, problem sets, coding snippets) is distributed through this repository. Your own solutions go into a separate repository that we set up together in class.

## Before the first session

Please complete the steps below **before 10.09.2026**. Setting up software is sometimes tricky across operating systems, and we lose a lot of class time if we do it live. If you get stuck, send me an email with the error message and I will help you sort it out before the course starts.

The short version:

1. [Create a GitHub account](#1-github-account) and apply for the Student Developer Pack
2. [Install Git](#2-git)
3. [Install GitHub Desktop](#3-github-desktop)
4. [Install VS Code](#4-vs-code) with the Julia, Python, and Jupyter extensions
5. [Install Julia](#5-julia) and/or [Python](#6-python)
6. [Run the checks](#7-check-that-everything-works) at the end of this page
7. Bring a laptop to every session, a good part of the course is spent writing code together

The templates I hand out are written in Julia and in Python. You can in principle work in any language, but I strongly advise you to stick with one of these two. You do not need both, pick the one you are more comfortable with (or want to learn).

## 1. GitHub account

1. Create an account at [github.com](https://github.com/) if you do not have one. Use a username you are happy to keep, it will be visible to your fellow students.
2. Apply for the [GitHub Student Developer Pack](https://education.github.com/pack). It is free for students and includes GitHub Copilot, which we use in the AI-assisted coding module. Verification requires a university email address or proof of enrollment and **approval can take a few days**, so apply early.
3. Once the pack is approved, activate Copilot at [github.com/settings/copilot](https://github.com/settings/copilot).

## 2. Git

Git is the version control system underneath GitHub. You submit all problem sets through it.

**Windows:** download and run the installer from [git-scm.com/downloads](https://git-scm.com/downloads). The default options are fine. When asked about the default editor, pick VS Code if it is already installed. When asked about line endings, keep "Checkout Windows-style, commit Unix-style".

**macOS:** open the Terminal and type `git --version`. If Git is not installed, macOS offers to install the Command Line Tools, accept that. Alternatively use the installer from [git-scm.com/downloads](https://git-scm.com/downloads) or `brew install git` if you use Homebrew.

**Linux:** install through your package manager, for example `sudo apt install git` on Ubuntu or Debian.

After installing, open a terminal (on Windows: Git Bash or PowerShell) and tell Git who you are. Use the same email address as for your GitHub account:

```
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

## 3. GitHub Desktop

GitHub Desktop is a graphical interface for Git. We use it in class so that nobody has to memorize commands in week one. You are welcome to use the command line or the Git integration in VS Code instead once you are comfortable.

1. Download and install from [desktop.github.com](https://desktop.github.com/).
2. Start it and sign in with your GitHub account (File, Options on Windows, GitHub Desktop, Settings on macOS).
3. Under Git in the same settings dialog, check that your name and email are filled in.

Linux users: GitHub Desktop has no official Linux build. Use the community build from [github.com/shiftkey/desktop](https://github.com/shiftkey/desktop) or simply work with Git from the command line or from VS Code.

## 4. VS Code

VS Code is the editor we use in class for Julia and Python.

1. Download and install from [code.visualstudio.com](https://code.visualstudio.com/). On Windows, keep the option "Add to PATH" checked.
2. Open VS Code, open the Extensions view (icon on the left bar, or `Ctrl+Shift+X`, on macOS `Cmd+Shift+X`) and install:
   - **Julia** (by julialang) if you work in Julia
   - **Python** (by Microsoft) if you work in Python
   - **Jupyter** (by Microsoft), needed for notebooks in both languages
   - **GitHub Copilot** and **GitHub Copilot Chat** (by GitHub), once your Student Developer Pack is approved
   - Optional but useful: **GitLens** (Git history inside the editor) and **Rainbow CSV**
3. If you installed VS Code before Git, restart VS Code so that it finds Git.

## 5. Julia

Install Julia through `juliaup`, the official version manager. It lets you update Julia and keep several versions side by side, which matters for reproducibility.

**Windows:** open PowerShell or a terminal and run

```
winget install --name Julia --id 9NJNWW8PVKMN -e -s msstore
```

(or install "Julia" from the Microsoft Store).

**macOS and Linux:** open a terminal and run

```
curl -fsSL https://install.julialang.org | sh
```

Accept the defaults. Then close and reopen the terminal.

Check that it works by typing `julia` in a fresh terminal. You should see the Julia banner and a `julia>` prompt. Check the version with `versioninfo()`, it should be the current stable release (1.11 or newer). Exit with `exit()` or `Ctrl+D`.

You do not need to install any packages before the first session. The templates ship with a `Project.toml` and `Manifest.toml` that pin the exact package versions, and we cover how to use those in class.

Finally, connect VS Code to Julia. The Julia extension usually finds a `juliaup` installation on its own. If it does not, open the VS Code settings (`Ctrl+,`), search for `julia executable path` and enter the path shown by `which julia` (macOS, Linux) or `where julia` (Windows).

## 6. Python

Install Python through Anaconda or Miniconda. Both give you the `conda` package manager, which we use later to create an isolated environment for the course.

- **Anaconda** is the full distribution. It is a large download (several GB) but comes with all scientific packages preinstalled and a graphical launcher. Choose this if you prefer clicking over typing.
- **Miniconda** is the minimal version. It installs only Python and `conda`, and you add packages as you need them. Choose this if you want a lean setup or already know your way around a terminal.

Either one is fine for the course. Download the installer for your operating system from [anaconda.com/download](https://www.anaconda.com/download) (the page asks for an email address, there is a small "skip registration" link) and run it with the default options. On Windows, do not add Anaconda to the PATH when the installer warns against it, use the "Anaconda Prompt" from the start menu instead.

Check that it works by opening a terminal (Windows: Anaconda Prompt) and typing `conda --version` and `python --version`. Both should print a version number.

You do not need to install any packages before the first session. The templates ship with an environment file that pins the exact package versions, and we cover how to use it in class.

Finally, tell VS Code to use this Python. Open any `.py` file, click on the Python version in the bottom status bar (or run "Python: Select Interpreter" from the command palette, `Ctrl+Shift+P`) and pick the Anaconda or Miniconda installation.

## 7. Check that everything works

Work through this list. If any item fails, email me with the error message and your operating system.

- [ ] I can log in at github.com and I have applied for the Student Developer Pack
- [ ] `git --version` in a terminal prints a version number
- [ ] `git config --global user.name` prints my name
- [ ] GitHub Desktop opens and shows me as signed in
- [ ] VS Code opens and the extensions listed above are installed
- [ ] Julia: `julia` starts and `1 + 1` at the prompt returns `2`
- [ ] Python: `conda --version` and `python --version` print version numbers
- [ ] VS Code runs a Julia file or a Python file (create a file with `println("hello")` or `print("hello")` and run it)

A good end-to-end test: clone this repository. In GitHub Desktop choose File, Clone repository, paste `https://github.com/Fabio-Stohler/E8069-Computational-Macro`, and pick a folder on your laptop. Then open that folder in VS Code (File, Open Folder). If you see the files of this repository in the VS Code sidebar, you are ready for the first session.

If something does not work, close and reopen the terminal first (installers change the PATH and open terminals do not notice). If that does not help, email me with the error message and your operating system.

## Repository structure

All code comes in two versions with the same content, one in Julia and one in Python. Go to the folder of the language you work in, each has its own README with setup instructions and an overview of the files.

```
E8069-Computational-Macro/
├── README.md            this file
├── Syllabus.pdf         course plan, assessment, literature
├── Julia/               Julia track: environment (Project.toml) and one folder per week
│   ├── README.md
│   └── Week_1/          Week_1_primer.ipynb: vectors, functions, structs, plotting, VFI by hand on a grid
├── Python/              Python track: environment (environment.yml) and one folder per week
│   ├── README.md
│   └── Week_1/          Week_1_primer.ipynb: vectors, functions, classes, plotting, VFI by hand on a grid
└── projects/            information on the final project (later in the semester)
```

The repository fills up over the semester. Problem set templates (gap texts) and coding snippets go into the weekly folders of both language tracks.

## Week 1 primer

Before session 2, work through the notebook `Week_1_primer.ipynb` in `Julia/Week_1` or `Python/Week_1`. Its five parts introduce, in this order, arrays and broadcasting, functions and the loop with a convergence criterion, containers for parameters and grids, plotting, and the Bellman operator on a grid. Every file uses the growth model from the dynamic programming review of session 1 (log utility, production `k^alpha`, full depreciation): the loops iterate the recursion `F_{n+1} = alpha + alpha beta F_n` and the saving rate map from the slides, the analytical solution `k' = alpha beta k^alpha` serves as the benchmark, and the last file redoes the "VFI by hand" slide on a grid for `n = 1, 2, 3`. Session 2 turns that into value function iteration, which is also what problem set 1 asks for. Each part ends with three short exercises, they are not graded.

## Problem sets and the final project

Problem sets are solved in teams of two and submitted through GitHub. Deadlines are Sundays at 23:59: 27.09. (PS 1), 11.10. (PS 2), 25.10. (PS 3), and 22.11.2026 (PS 4). The midterm takes place in class on 29.10.2026. The final project (repository and write-up) is due on 13.12.2026 at 23:59, after the project presentations on 10.12. See the syllabus for details on grading and the AI policy.

## License

The material in this repository is released under the [MIT License](LICENSE).
