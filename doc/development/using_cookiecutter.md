## Cookiecutter

"Cookiecutter is an open source library for building coding project templates" [see cookiecutter.io](https://www.cookiecutter.io/).

## cookiecutter-openalea

[cookiecutter-openalea](https://github.com/openalea/cookiecutter-openalea/) is a template for OpenAlea packages that
follows the [OpenAlea development guidelines](./guidelines.md), and provides all necessary files and configurations to 
develop a new package up to the continuous integration and package publication on a conda channel.

## Typical workflow

1. Create a new package using `cruft create https://github.com/openalea/cookiecutter-openalea/`
2. Initiate your git repository: `git init` (needed for `setuptools_scm` to work properly)
3. Install the package in editable mode with dev dependencies: `mamba env create -f conda/environment.yml`
4. Activate the environment: `mamba activate my_project_dev` # Replace `my_project` with your project slug defined in `cookiecutter.json`
5. Implement your package code in the `src/` directory, add your tests in the `tests/` directory, and documentation in the `doc/` directory.
6. Build the documentation: `cd doc && make html`
7. Run tests: `pytest`

## How to create a new OpenAlea package from existing code

Let's consider the following code `mycode.py`:
```python
import numpy as np
import pandas as pd

from openalea.plantgl.algo.view import view
from openalea.plantgl.all import *

view(Sphere())

a = np.array([1,2,3])

d = pd.DataFrame(a)
```

And we want to integrate it into an OpenAlea project that follows the [guidelines](./guidelines.md).

### Creating "a blanc" project

Not mandatory but first create a conda environment with necessary package:
```bash
mamba create -n myenv -c conda-forge cruft
mamba activate myenv
```

Then create the new project, let's say we want `myproject` to be locally created in `/home/dev`, therefore in this directory
run the following and answer the questions:
```bash
cruft create https://github.com/openalea/cookiecutter-openalea/
```
For example here the kind of output:
```
  [1/8] full_name (Jane Doe): Firstname Lastname
  [2/8] email (jane.doe@example.com): first.last@example.com
  [3/8] github_username (openalea-incubator): ghusername
  [4/8] project_name (python_project_name): MyProject
  [5/8] project_slug (myproject): myproject
  [6/8] description (Project short description.): this is an example           
  [7/8] pure_python [y/n] (y): 
  [8/8] version (0.0.1):
```

At this stage 
```bash
MyProject/
├── AUTHORS.md
├── CHANGELOG.md
├── CITATION.cff
├── conda
│   ├── environment.yml
│   └── meta.yaml
├── CONTRIBUTING.md
├── doc
│   ├── api.md
│   ├── conf.py
│   ├── examples
│   │   ├── example1.ipynb
│   │   └── example2.ipynb
│   ├── extra.md
│   ├── index.md
│   ├── installation.md
│   ├── Makefile
│   └── usage.md
├── LICENSE
├── MANIFEST.in
├── pyproject.toml
├── README.md
├── src
│   └── openalea
│       ├── myproject
│       │   └── __init__.py
│       └── myproject_wralea
│           └── __init__.py
└── test
    ├── __init__.py
    └── test_myproject.py
```
Now let's incorporate our code. According to `mycode.py` there are the following dependencies **numpy**, **pandas** and
**openalea.plantgl**. `conda/environment.yaml` and `pyproject.toml` must be updated.
```yaml
name: myproject_dev
channels:
  - conda-forge
  - openalea3
dependencies:
  - python
  - pip
  - numpy
  - pandas
  - openalea.plantgl
  - pip:
      - -e '..[test,dev,doc]'
```
In the section `[project]` of the `pyproject.toml` we add the non openalea dependencies
```toml
...
[project]
name = "openalea.myproject"
...
dependencies = [
  "numpy",
  "pandas",
]
```
In the section `[tool.conda.environment]` of the `pyproject.toml` we add the openalea dependencies
```toml
...
[tool.conda.environment]
...
dependencies = [
    "openalea.plantgl",
]
```



