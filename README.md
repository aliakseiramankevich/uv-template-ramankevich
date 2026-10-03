# uv-template-ramankevich

## A brief explanation of what uv is and how it works.
uv is fast Python package and project manager. It is designed to replace a stack of separate tools such as pip, virtualenv, pip-tools, pipx, pyenv, with one command-line program.

uv can manage most common Python-development tasks: install and select Python versions, create isolated virtual environments, install project dependencies, resolve compatible dependency versions and write a reproducible lockfile, run Python scripts and CLI tools in controlled environments.

A typical project with uv uses:
 - pyproject.toml - declares the project and its dependencies.
 - uv.lock - records the exact resolved versions, so another machine or CI environment gets the same dependency graph.

When you request a dependency (e.g. uv add numpy) uv:
 - Updates the dependency declaration in pyproject.toml.
 - Resolves a mutually compatible set of package versions, including transitive dependencies.
 - Saves that exact solution to uv.lock.
 - Creates or updates the project .venv virtual environment.
 - Downloads/install packages from Python package indexes as needed.


## Instructions on how to install dependencies using uv.

Creating and running new project
```bash
# Create a new project
uv init my-project
cd my-project

# Adding dependencies
uv add numpy pandas

# Adding dependencies with constraints
uv add "torch>=2.3,<3"
uv add "requests==2.31.0" 

# Run a program inside the managed environment
uv run python main.py
```

To install a project dependencies with uv, go to the directory containing pyproject.toml and run
```bash
uv sync
```

If you are migrating a project from pip to uv
```bash
uv add -r requirements.txt
uv sync
```


## Sequence of git commands
Cloning repository
```bash
git clone https://github.com/aliakseiramankevich/uv-template-ramankevich
```
---
Creating dev branch
```bash
git checkout -b dev
```
---
Pushing uv initialization into dev branch
```bash
git add .
git commit -m "init uv, add uv dependencies"
git push --set-upstream origin dev
```
---
Creating feature/setup branch
```bash
git checkout -b feature/setup-tests
```
---
Pushing tests realization into dev branch
```bash
git add .
git commit -m "added pytests"
git push --set-upstream origin feature/setup-tests
```
---
Adding Makefile into dev branch
```bash
git checkout dev 
git add Makefile
git commit -m "Added Makefile"
git push
```
---
Updating feature/setup branch to dev branch state
```bash
git checkout feature/setup-tests
git fetch origin
git rebase origin/dev
git push -f
```
---
Pushing changes with bad test
```bash
git add .
git commit -m "added tests"
git push
```
---
Undoing bad commit
```bash
git log
git revert HEAD~0
```
---
Pusing right test realization
```bash
git add .
git commit -m "fixed test"
git push
```
---
Merging dev branch with feature/setup-tests branch
```bash
git checkout dev
git merge feature/setup-tests
```
---
```bash
git add .
git commit -m "Upadated README"
git push
```
