## Cookiecutter

"Cookiecutter is an open source library for building coding project templates" [see cookiecutter.io](https://www.cookiecutter.io/).

## cookiecutter-openalea

[cookiecutter-openalea](https://github.com/openalea/cookiecutter-openalea/) is a template for OpenAlea packages that
follows the [OpenAlea development guidelines](./guidelines.md), and provides all necessary files and configurations to 
develop a new package up to the continuous integration and package publication on a conda channel.

## How to create a new OpenAlea package from existing code

Let's consider the following code `mycode.py`:
```python
import numpy as np
import pandas as pd

from openalea.plantgl.algo.view import view
from openalea.plantgl.all import *

def display_sphere():
    view(Sphere())

def list_to_array(l):
    return np.array(l)

def array_to_df(a):
    return pd.DataFrame(a)
```

And we want to integrate it into an OpenAlea project that follows the [guidelines](./guidelines.md).

### Creating "a blanc" project

Not mandatory but recommended, first create a conda environment with `cruft` and `python` package:
```commandline
mamba create -n myenv -c conda-forge cruft python=3.12
mamba activate myenv
```

Then create the new project, let's say we want `myproject` to be locally created in `/home/dev`, therefore in this directory
run the following command and answer the questions:
```commandline
cruft create https://github.com/openalea/cookiecutter-openalea/
```
For example, here the kind of output:
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

Then init the git repository:
```commandline
git init -b main
```

At this stage, the local directory looks as follows:
```bash
MyProject/
├── AUTHORS.md
├── CHANGELOG.md
├── CITATION.cff
├── conda
│   ├── environment.yml
│   └── meta.yaml
├── CONTRIBUTING.md
├── .coveragerc
├── .cruft.json
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
├── .github
│   └── workflows
│       └── conda-package-build.yml
├── .gitignore
├── LICENSE
├── MANIFEST.in
├── pyproject.toml
├── README.md
├── .readthedocs.yml
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

### Incorporating existing code
Now let's incorporate our code. According to `mycode.py` there are the following dependencies **numpy**, **pandas** and
**openalea.plantgl**. `conda/environment.yaml` and `pyproject.toml` can be updated as follows:
The dependencies are added to the section **dependencies** of `conda/environment.yaml`

```yaml
name: myproject_dev
channels:
  - conda-forge
  - openalea3
dependencies:
  ...
  - numpy
  - pandas
  - openalea.plantgl
  ...
```
In the section `[project]` of the `pyproject.toml` file we add the non openalea dependencies
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
In the section `[tool.conda.environment]` of the `pyproject.toml` file we add the openalea dependencies
```toml
...
[tool.conda.environment]
...
dependencies = [
    "openalea.plantgl",
]
```

### Create test
Cruft has created a directory `test` and a file `test_myproject.py`. Complete and modify it to test the project, for example:
```python
from openalea.myproject import mycode

def test_functions():
    l = [1.0, 2.0, 3.0]
    a = mycode.list_to_array(l)
    d = mycode.array_to_df(a)
    assert l == a.tolist()
```

### Building and testing locally the packqge
Now let's locally build the package. First install the necessary packages:
```commandline
mamba install conda-build pytest
```
Then in the root directory of the project run:
```commandline
conda-build conda -c conda-forge -c openalea3
```

Once the package builds correctly with test passed, it is possible to push MyProject to a remote repository.
Before that the remote repository must be created. Let's assume `MyProject` was created on `openalea-incubator`.
The project can then be pushed as follows:
```bash
git status # to check the changes
git add . # to add all files that changed
git commit -m '1st commit' 
git remote add origin https://github.com/openalea-incubator/MyProject.git 
git push -u origin main
```

### Doc, examples, etc.
Adapt, change doc and examples as you need.