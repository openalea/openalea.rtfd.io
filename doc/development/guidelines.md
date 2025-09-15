# OpenAlea development guidelines

```{Important}
___Definition___: Coding rules, or good practices, or coding conventions, aiming at  uniforming source code in a project.
```

## Why guidelines ?

__Quality__:

- code is easier to read: of particular importance for users and when developing within a team
- code is more robust: easier to debug and modify
- act as in "quality insurance" for users

__Deployment__:

- uniformization of procedures
- deployment made easier -> easy installation for end-users

__Diffusion__:

- unique release
- gain in code and software visibility

## Guidelines in OpenAlea

Within OpenAlea, we have defined a set of minimal and limited guidelines that are important to improve homogeneity and quality between packages. These guidelines are __highly__ recommended for all developers, and in particular, new ones.

These guidelines are used to ensure the quality of the code and to facilitate the deployment and diffusion of the software. It also simplify global OpenAlea support and maintenance.
Same guidelines should be applied to all OpenAlea projects and are detailed below.

Although OpenAlea guidelines are limited to ensure that scientific developers can easily contribute to the project, we encourage developers to follow more general guidelines, when OpenAlea guidelines are missing. This allow to get in sync with the Scientific Python Community. Very good examples can be found in:

- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html) : set of rules for writing clear and readable Python code used at Google.
- [Python package guide](https://www.pyopensci.org/python-package-guide/index.html) : guide for developing Python packages for open science. Best practices and recommendations for developing Python packages.
- [Packaging Python](https://packaging.python.org/en/latest/) : collection of tutorials and references to help you distribute and install Python packages with modern tools.
- [Learn Scientific Python](https://learn.scientific-python.org/development/) : guide for writing maintainable, reusable, and shareable Python package for scientific computing.

## Package layout and namespace

- All [OpenAlea](https://github.com/openalea) and [OpenAlea-incubator](https://github.com/openalea-incubator) projects should use 'openalea' as a global namespace, to manifest their belonging to openalea initiative. Importing an openalea package will therefore always look like:

```python
from openalea.pkg_name import module_name
```

- Also, we recommend to use the [src-layout](https://setuptools.pypa.io/en/latest/userguide/package_discovery.html#src-layout) for the source code of the project.
  That yield the following basic layout for your package:

```bash
pkg_name
├── CHANGELOG.md               ┐
├── CODE_OF_CONDUCT.md         │
├── CONTRIBUTING.md            │
├── README.md                  │ Package metadata and build configuration
├── LICENSE                    │
├── pyproject.toml             ┘
├── doc                        ┐
│   └── index.md               │
│   └── ...                    │  Package documentation
│   └── examples               │
│   └──── notebook1.ipynb      │
│   └──── ...                  ┘
├── src                        ┐
│   └── openalea/pkg_name      │
│       ├── __init__.py        │ Package source code
│       ├── moduleA.py         │
│       └── moduleB.py         ┘
└── test                       ┐
   └── ...                     ┘ Package tests
```

Some mandatory files should be included at the root of the project.

### README.md

This is a very important file as it is the landing page of the project's code repository (`Github`) or on repository sites such as [PyPI](https://pypi.org/) or [Anaconda](https://anaconda.org/).

The README file should include the following information:

- the name of the project / package with a short and easy-to-understand description of what it does.
- badges to show the status of the project, *e.g.*:
  - documentation status: [![Docs](https://readthedocs.org/projects/mtg/badge/?version=latest)](https://mtg.readthedocs.io/)
  - CI/CD status: [![Build Status](https://github.com/openalea/mtg/actions/workflows/conda-package-build.yml/badge.svg?branch=master)](https://github.com/openalea/mtg/actions/workflows/conda-package-build.yml?query=branch%3Amaster)
  - Compatible `Python` version: [![Python Version](https://img.shields.io/badge/python-3.8%20%7C%203.9%20%7C%203.10%20%7C%203.11%20%7C%203.12-blue)](https://www.python.org/downloads/)
  - License: [![License](https://img.shields.io/badge/License--CeCILL-C-blue)](https://www.cecill.info/licences/Licence_CeCILL-C_V1-en.html)
  - Version of the package on Anaconda: [![Anaconda-Server Badge](https://anaconda.org/openalea3/mtg/badges/version.svg)](https://anaconda.org/openalea3/mtg)
 
```md
# Package Name
[![Docs](https://readthedocs.org/projects/mtg/badge/?version=latest)](https://mtg.readthedocs.io/)
[![Build Status](https://github.com/openalea/mtg/actions/workflows/conda-package-build.yml/badge.svg?branch=master)](https://github.com/openalea/mtg/actions/workflows/conda-package-build.yml?query=branch%3Amaster)
[![Python Version](https://img.shields.io/badge/python-3.8%20%7C%203.9%20%7C%203.10%20%7C%203.11%20%7C%203.12-blue)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License--CeCILL-C-blue)](https://www.cecill.info/licences/Licence_CeCILL-C_V1-en.html)
[![Anaconda-Server Badge](https://anaconda.org/openalea3/mtg/badges/version.svg)](https://anaconda.org/openalea3/mtg)
## Description
```
- installation instructions: how to install the package for user (using `conda` / `mamba`) and for developer (using `conda` / `mamba` and `pip -e`). For more information about how to declare package dependencies for usage and development, cf. [pyproject.toml](#pyprojecttoml) and [build the package](#building-the-package) sections.
```bash
# for user
mamba create -n myenv -c openalea3 -c conda-forge openalea.my_pkg openalea.plantgl

# for developer, in an existing environment
git clone 'https://github.com/openalea/my_pkg.git'
cd my_pkg
mamba install --only-deps -c openalea3 -c conda-forge openalea.my_pkg
pip install -e .[options]
# [options] is optional, and allows to install additional dependencies 
# defined in the [project.optional-dependencies] section of your 
# pyproject.toml file (usually "dev", or "doc", ...)

# (optionaly) for maintainer that need clean isolated env, or to start development (i.e. before first build)
# (see conda section below on how to write environment.yml file)
mamba env create -f ./conda/environment.yml
```

- usage instructions: how to use the package, with a brief and simple example.
- links to the documentation, the license, the code of conduct, the contributing guidelines, and the changelog.
- Citation information: how to cite the package in a scientific publication.

### LICENSE

This file should include the license of the project. The license recommended for OpenAlea package is the [CeCILL-C](https://www.cecill.info/licences/Licence_CeCILL-C_V1-en.html) license:

- the [CeCILL-C License](https://www.cecill.info/licences/Licence_CeCILL-C_V1-en.html) : a copyleft, Free Software license that is compatible with French Law. The license is similar to the [L-GPL](https://choosealicense.com/licenses/lgpl-3.0/).

If you want to choose another license, please contact the OpenAlea developer team to be sure that your license is compatible with the one of other packages.

### CONTRIBUTING.md

This file should include information on how to contribute to the project: how to report bugs, how to request new features, how to ask questions and how to submit code changes.

### CODE_OF_CONDUCT.md

This document will help building a community around your package. It sets what you expect from the users and contributors of the project, in terms of behavior and communication. You can check examples on the web, such as [scikit-learn](https://github.com/scikit-learn/scikit-learn/blob/main/CODE_OF_CONDUCT.md).

### CHANGELOG.md

This file should be a resource for developers anf users to know what has changed in the project over time. It should include a list of changes for each version of the project.

## Versioning

- We recommend delegating the versioning of your package to the version control system (eg git), by using semantic versionning tags starting with `v`.
[Semantic vernioning tags](https://semver.org/) are of the form : Major.minor.patch. Using CI, every time a new tag is created and merged in the master branch,
a new conda package will be uploaded on conda-forge using that tag as version number.
- This tag can also be retrieved automatically by your build system (declared in pyproject) to correctly fill your package metadata and provide user or tools a way to access the version using importlib
- Optionally (but still recommended), for convenience, you can expose the version to user/tools by setting the __version__ attribute of your package in its src/openalea/my_pkg/__ini__.py file:

```python
# add this in src/openalea/my_pkg/__init__.py:
from importlib.metadata import version, PackageNotFoundError

try:
    __version__ = version("openalea.my_pkg")
except PackageNotFoundError:
    # package is not installed
    pass
```

- To avoid confusion all other manual reference to version (version.py files,...) should be removed from your source tree

## pyproject.toml

OpenAlea projects should use the `pyproject.toml` file to define the build configuration and the metadata of the project.
This file should contain the following sections:

- In most cases you can use [`setuptools` as the build system](https://setuptools.pypa.io/en/latest/). `setuptools` is the most widely used build system for Python packages. It is used to define the metadata of the package, the dependencies, and the entry points.
We also recommend using setuptools_scm as a companion tool to handle automatically set the version metadata of your package based on git tags.

```toml
[build-system]
requires = [
    "setuptools",
    "setuptools_scm",
]
build-backend = "setuptools.build_meta"

# where your source lies if you followed src layout
[tool.setuptools.packages.find]
where = ["src"]

[tool.setuptools]
include-package-data = false # force explicit declaration of data (disable automatic inclusion)

# enable dynamic version based on git tags
[tool.setuptools_scm]
# Format version to ease alignment with conda/meta.yaml tag-based versioning
fallback_version = "0.0.0.dev0"
version_scheme = "guess-next-dev"
local_scheme = "no-local-version"
```

If your package needs an extension module, you should check the [dedicated `setuptools` documentation](https://setuptools.pypa.io/en/latest/userguide/ext_modules.html#building-extension-modules)

- Define the metadata of the project in the `[project]` section.
This metadata should include the name of the project, the authors, the description, the README file, the license file,
the Python version required, the classifiers, the dynamic metadata, and the dependencies that can be found on pypi.
For dependency that are distributed via conda only (like all openalea package), please use a separate section to keep your pyproject fully functionnal with pip

```toml
[project]
name = "openalea.pkg_name"
authors = [
  { name = "Jane Doe", email = "jane.doe@mail.com" },
  ...
]
description = "FSPM tools for OpenAlea"
readme = "README.md"
license = "CECILL-C"
license-files = ["LICEN[CS]E*"]
requires-python = ">=3.10"
dynamic = ["version"]
classifiers = [
  "Development Status :: 1 - Planning",
  "Intended Audience :: Science/Research",
  "Intended Audience :: Developers",
  "License :: OSI Approved :: CeCILL-C License",
  "Operating System :: OS Independent",
  "Programming Language :: Python",
  "Programming Language :: Python :: 3",
  "Programming Language :: Python :: 3 :: Only",
  "Programming Language :: Python :: 3.10",
  "Programming Language :: Python :: 3.11",
  "Programming Language :: Python :: 3.12",
  "Topic :: Scientific/Engineering",
  "Framework :: OpenAlea",
]

# you can list here all dependencies that are pip-instalable, and that have a name identical to the one used by conda (to allow reuse of this list in meta.yaml)
# If conda name is different, please do not declare the pip name, and declare conda name in the next section
dependencies = [
    "numpy >= 1.24",
    ...
]

# section specific to conda-only distributed package (not used by pip yet)
[tool.conda.environment]
channels = [
  "openalea3",
  "conda-forge"
]
dependencies = [
    "openalea.plantgl",
    "openalea.mtg",
    ...
]
```

- Additionally, you can define the optional dependencies for development mode and test mode in the [`[project.optional-dependencies]` section](https://setuptools.pypa.io/en/latest/userguide/dependency_management.html#optional-dependencies).

```toml
[project.optional-dependencies]
test = [
  "pytest",
  "nbmake",
  ...
]
dev = [
  "pytest >=6",
  "pytest-cov >=3",
]
doc = [
  "pydata-sphinx-theme",
  "myst-parser",
  "sphinx-favicon",
  "ipykernel",
  "sphinx-copybutton",
  "ipython_genutils",
  "nbsphinx",
]
```

- Define the URLs of the project in the `[project.urls]` section.

```toml
[project.urls]
Repository = "https://github.com/openalea/pkg_name"
Homepage = "https://pkg_name.readthedocs.io/"
"Bug Tracker" = "https://github.com/openalea/pkg_name/issues"
Discussions = "https://github.com/openalea/pkg_name/discussions"
Changelog = "https://github.com/openalea/pkg_name/releases"
```

- Declare your entry point, eg the location of the directory containing the __wralea__ file:

```toml
[project.entry-points."wralea"]
"my_pkg" = "openalea.my_pkg_wralea"
```

## Package Resources / Data files

You might want to include resources/data files (i.e. any files that is not a *.py file) in your package for a number of reasons, that will determine your packaging strategy:

- the resource is mandatory for your python source code to run (eg a dll or a template file) => include it as a package resource (see [Distributing as a package resource](#distributing-as-a-package-resource) section)
- the resource is mandatory for your python source code to run, but is too large in size for github (eg a trained deep-learning model) => refer it as an external resource in the code (see [Distributing as an external resource](#distributing-as-an-external-resource) section)
- the resource is only used in tests (and is relatively small in size) => add a `test/data dir` and access it with relative path (see [Direct access using relative paths](#direct-access-using-relative-paths) section)
- the resource is only used in notebooks (and is relatively small in size) => add a `doc/examples/data` dir and access it with relative path (see [Direct access using relative paths](#direct-access-using-relative-paths) section)
- the resource is accessed by test and notebooks (and is relatively small in size) => include it as a package resource (see [Distributing as a package resource](#distributing-as-a-package-resource) section)
- the resource is accessed by test, notebooks, and/or is usefull for other packages (eg database), and/or is composed of large file (e.g. phenotyping images) => refer it as an external resource in the code (see [Distributing as an external resource](#distributing-as-an-external-resource) section)

### Direct access using relative paths

This method is recommended only if you are sure that the data files will be accessed by cloning the git repository (e.g. clone/run tests locally or on CI runners, clone/build doc locally or by ReadTheDoc runner).
It can also work for data located in source dir (e.g src/openalea/pkg_name/data), but it is not recommended, as some build tools will zip the src dir and defeat the method. In the later case prefer [Distributing as a package resource](#distributing-as-a-package-resource).Ò

This method is pretty straightforward, as you just have to add a data dir, e.g. for test:

```bash
pkg_name
├── ...
├── test
│   ├── test_A.py
│   ├── data
│       ├── data_file_A.csv
```

and in test_A.py, access the data file with:

```python
from pathlib import Path
this_dir = Path(__file__).parent if '__file__' in globals() else Path(".").resolve()
data_dir = this_dir.parent / "data"
data_A_path = data_dir / "data_file_A.csv"
```

### Distributing as a package resource

This approach is detailed in [`setuptools` documentation](https://setuptools.pypa.io/en/latest/userguide/datafiles.html#accessing-data-files-at-runtime). This approach should be preferred to a direct manipulation of the package’s \_\_file\_\_ attribute, as the later can fail if your data are distributed via zip, egg or wheels.

The recommended way of organising your data is to add a data folder in your package source folder, and declare the ressources in pyproject.toml:

```bash
pkg_name
├── ...
├── pyproject.toml               ] declaration of package data
├── src                          ┐
│   └── openalea/pkg_name        │
│       ├── __init__.py          │ Package source code
│       ├── moduleA.py           │
│       └── moduleB.py           ┘
|       └── data                    ┐
|          ├── data_fileA.csv       |
|          └── data_fileB.csv       | Data files
|          └── data_subdir          |
|            └──data_fileC.csv      ┘
```

In pyproject.toml you will use the package-data section to specify which files are to be included. It could be as simple and generic as :

```toml
# pyproject.toml
[tool.setuptools.package-data]
"openalea.pkg_name" = ["data/**/*"]
```

This method is fully compatible with the recommended 'include-package-data = false' directive, that only force explicit data declaration.

You can then access data using importlib.resources. It is currently recommended to use `importlib_resources` backport module for Python 3.7 and above, as importlib.resources only works for python 3.10 and above. The only difference is to replace the underscore by a point in the following examples.:

```python
from importlib.resources import files, as_file

datadir = files('openalea.pkg_name.data')
# return the list of files present in the data dir:
data = list(datadir.iterdir())

# return the content of the resource named 'data_fileA.csv':
data1 = (datadir / 'data_fileA.csv').read_text()

# read the content using pandas read_csv reader
import pandas
with as_file(datadir / 'data_fileA.csv') as p:
   data1 = pandas.read_csv(p)
```

### Distributing as an external resource

This strategy implies posting the raw data on a dedicated public repository (e.g. [GitHub](https://github.com) or [Zenodo](https://zenodo.org/)), and provide access to these resources using [Pooch](https://www.fatiando.org/pooch).
Pooch will retrieve in a secured manner the remote files and store them in your local cache, so that the download time is paid only once (like cloning a data repo) and nly for the data you need (unlike cloning).
Pooch also detect if your local cached version differs from the remote one and handle it as expected.
An example of a package using this strategy can be found in [openalea.phenotyping_data](https://github.com/openalea/phenotyping_data). The key part of the code lies in the fetch.py module, that can refer to any url, and not only to data located in the package.

```python
from pathlib import Path
from importlib.resources import files, as_file
import pooch

REGISTRY = files('openalea.phenotyping_data') / 'registry.txt'
BASE_URL = "https://raw.githubusercontent.com/openalea/phenotyping_data/main/data/"
POOCH = pooch.create(
    path=pooch.os_cache("phenotyping_data"),
    base_url=BASE_URL,
    version_dev="main",
    # We'll load it from a file later
    registry=None,
)
with as_file(REGISTRY) as registry_path:
    POOCH.load_registry(registry_path)


def fetch_data(filename):
    return POOCH.fetch(filename)


def list_data(prefix=""):
    return [name for name in POOCH.registry if name.startswith(prefix)]


def fetch_all_data(prefix=""):
    for filename in list_data(prefix):
        fetch_data(filename)

    data_dir = Path(str(POOCH.abspath)) / prefix

    return data_dirÒ
```

Data can then be retrieved using,e.g.

```python
from openalea.phenotyping_data.fetch import fetch_data, list_data, fetch_all_data
list_data()
path = fetch_data('plant_1/raw/side/0.png')
datadir = fetch_all_data('plant_1/raw')
```

## Building the package

The package should be installable using the [`conda` package manager](https://docs.conda.io/projects/conda/en/latest/index.html) and `conda / mamba` commands, from the [`openalea3` conda channel](https://anaconda.org/openalea3), e.g.:

```bash
mamba install -c openalea3 -c conda-forge openalea.pkg_name openalea.plantgl numpy
```

```{Note}
We strongly recommend to use `mamba` instead of `conda` as it is much faster and less error-prone to versions conflicts.
```
Implications are that:

- all dependence should also be available from a conda channel or via `pip`.
- package should be built and uploaded to the `openalea3` conda channel. A [dedicated CI/CD pipeline](#ci-cd) can be used for this purpose.
- ensure that the version number match the node set in pyproject.toml (see example below for dynamic setuptools_scm version).

We also recommend re-using the information declared in your pyproject.toml to source only once your list of dependencies.

A minimal conda build information could be provided by adding the following generic conda/meta.yaml file at the root of your project:

```yaml
{% set pyproject = load_file_data('../pyproject.toml', from_recipe_dir=True) %}
{% set name = pyproject.get('project').get('name') %}
{% set description = pyproject.get('project').get('description') %}
{% set license = pyproject.get('project').get('license') %}
{% set home = pyproject.get('project', {}).get('urls', {}).get('Homepage', '') %}
{% set build_deps = pyproject.get("build-system", {}).get("requires", []) %}
{% set deps = pyproject.get('project', {}).get('dependencies', []) %}
{% set conda_deps = pyproject.get('tool', {}).get('conda', {}).get('environment', {}).get('dependencies',[]) %}

{# Align version with the one computed by setuptools_scm #}
{% set base_tag = GIT_DESCRIBE_TAG | default("0.0.0.dev0") | replace("v", "") %}
{% set distance = GIT_DESCRIBE_NUMBER | default("0") | int %}
{% set base_parts = base_tag.split('.') %}
{% set micro = base_parts[2] | int %}
{% set next_version = base_parts[0] + "." + base_parts[1] + "." + (micro + 1)|string %}
{% set scm_version = next_version + ".dev" + distance|string if distance > 0 else base_tag %}
{% set version = environ.get('SETUPTOOLS_SCM_PRETEND_VERSION', scm_version) %}

package:
  name: {{ name }}
  version: {{ version }}

source:
  path: ..

build:
  noarch: python
  preserve_egg_dir: True
  # pip install options mainly ensure that dependencies are handled by conda (and not pip)
  # --no-deps ensure pip will not install deps not declared in meta.yaml (but declared in pyproject.toml)
  # --no-build-isolation ensure pip will not replace build deps declared in meta.yaml (and declared in pyproject.toml)
  # --ignore-installed ensure that compiled files (accidentally present in sources or uncleaned locally) will be overwritten
  script: {{ PYTHON }} -m pip install . --no-deps --ignore-installed --no-build-isolation -vv

requirements:
  host:
    - python
    {% for dep in build_deps %}
    - {{ dep }}
    {% endfor  %}

  run:
    - python
    {% for dep in deps + conda_deps %}
    - {{ dep }}
    {% endfor %}

test:
  requires:
    - pytest
    - nbmake
  imports:
    - {{ name }}
  source_files:
    - test/test_*.py
    - doc/notebooks/*.ipynb
  commands:
   - pytest -v
   - pytest --nbmake

about:
  home: {{ home }}
  license: {{ license }}
  summary: {{ description }}
```

- You can also provide a conda/environment.yml file that will ease maintainers developing in a isolated environment, and can also be used by readthedoc:
-
```yaml
name: mypkg_dev
channels:
  - openalea3
  - conda-forge
dependencies:
  - python
  - pip
  - pandoc
# list here manually conda-only deps (listed in [tool.conda.environment] section of pyproject)
  - openalea.plantgl
# let pip install the rest using pyproject.toml (if you are okay with conda/pip mix)
  - pip:
      - -e ..[doc,test]
```

## CI-CD

CI/CD stands for Continuous Integration / Continuous Deployment. It is a set of practices and tools that allow to automate the building, testing, and deployment of the software.
It is a key practice for ensuring the quality of the software and the reliability of the deployment process.

Within the OpenAlea community, we use a custom-made [GitHub Actions](https://github.com/openalea/action-build-publish-anaconda) to build and deploy the packages to the `openalea3` conda channel.

The only thing you need to do is to add a `.github/workflows/conda-build.yml` file to your project with the following content:

```yaml
name: Building Package

on:
  push:
    branches:
      - '**'
    tags:
      - 'v*'
  pull_request:
    branches:
      - '**'


jobs:
  build:
    uses: openalea/github-action-conda-build/.github/workflows/conda-package-build.yml@main
    secrets:
      anaconda_token: ${{ secrets.ANACONDA_TOKEN }}
```

This action will build the package on a matrix of operating systems (`[ubuntu-latest , macos-latest , windows-latest]`) and Python versions (`[3.8, 3.9, 3.10, 3.11, 3.12]`) every time a new commit is pushed.

To enable a new upload to openalea3 conda channel, just create a tag/release starting with `v` on your github master.
To summarize we recommend the following development workflow: create branches, make pull request, review them, merge into master, and create a new tag release from github web interface.If you followed the guideline above, the tag wll be propagated to the package metadata and to the conda package.

## Documentation

The documentation of the package should be written using the [Sphinx](https://www.sphinx-doc.org/en/master/) documentation generator and hosted on the [ReadTheDocs](https://readthedocs.org/) platform.

To set up the ReadTheDocs documentation, you need to add a `.readthedocs.yml` file to the root of your project with the following content:

```yaml
version: 2

build:
  os: "ubuntu-22.04"
  tools:
    python: "mambaforge-22.9"

conda:
  environment: doc/environment.yml

sphinx:
  # Path to your Sphinx configuration file.
  configuration: doc/conf.py

```

This file will tell ReadTheDocs to build the documentation using the environment describe in the `doc/environment.yml` file (you can also use conda/environment.yml) and to set up the environment using `mambaforge`.

You just have then to log in with your github account to reedthedoc and add your project to your dashboard.

The documentation should be written in the `doc` folder of the package and should contain the following files:

- `conf.py`: the configuration file of the documentation, and how to build it. e.g.:

```python
# -*- coding: utf-8 -*-
import sys
import os

import pydata_sphinx_theme # Pydata theme: https://pydata-sphinx-theme.readthedocs.io/en/stable/index.html

from importlib.metadata import metadata
project='my_pkg'
meta = metadata('openalea.' + project)
release = meta.get("version")
# for example take major/minor
version = ".".join(release.split('.')[:3])
author = meta['Author-email'].split(' <')[0]
desc = meta['Summary']
urls = {k:v for k,v in [item.split(',') for item in meta.get_all('Project-URL')]}


# If extensions (or modules to document with autodoc) are in another directory,
# add these directories to sys.path here. If the directory is relative to the
# documentation root, use os.path.abspath to make it absolute, like shown here.
# sys.path.insert(0, os.path.abspath('.'))
sys.path.insert(0, os.path.abspath('..')) # to include the root of the package

# -- General configuration ------------------------------------------------
# Add any Sphinx extension module names here, as strings. They can be
# extensions coming with Sphinx (named 'sphinx.ext.*') or your custom
# ones.
extensions = [
    'sphinx.ext.autodoc',  # support for automatic inclusion of docstring
    'sphinx.ext.autosummary',  # generates autodoc summaries
    'sphinx.ext.doctest',  # inclusion and testing of doctest code snippets
    'sphinx.ext.intersphinx', # support for linking to other projects
    'sphinx.ext.mathjax',  # support for math equations
    'sphinx.ext.ifconfig',  # support for conditional content
    'sphinx.ext.viewcode',  # support for links to source code
    'sphinx.ext.coverage',  # includes doc coverage stats in the documentation
    'sphinx.ext.todo',      # support for todo items
    'sphinx.ext.napoleon',  # support for numpy and google style docstrings
    "sphinx_favicon",      # support for favicon
    "sphinx_copybutton",      # support for copybutton in code blocks
    "nbsphinx",     # for integrating jupyter notebooks
    "myst_parser"   # for parsing .md files
]
# Add any paths that contain templates here, relative to this directory.
templates_path = ['_templates']
autosummary_generate = True
exclude_patterns = ['build', '_build', '_templates']
# The suffix(es) of source filenames.
# You can specify multiple suffix as a list of string:
source_suffix = {
    '.rst': 'restructuredtext',
    '.md': 'markdown',
}
# The master toctree document.
master_doc = 'index'
# General information about the project.
copyright = u'Cecill-C INRAE / INRIA / CIRAD'
# The language for content autogenerated by Sphinx. Refer to documentation
# for a list of supported languages.
#
# This is also used if you do content translation via gettext catalogs.
# Usually you set "language" from the command line for these cases.
language = "en"
# The name of the Pygments (syntax highlighting) style to use.
pygments_style = 'sphinx'
# If true, `todo` and `todoList` produce output, else they produce nothing.
todo_include_todos = False

# -- Options for HTML output ----------------------------------------------
# The theme to use for HTML and HTML Help pages.  See the documentation for
# a list of builtin themes.
html_theme = 'pydata_sphinx_theme'
# Theme options are theme-specific and customize the look and feel of a theme
# further.  For a list of options available for each theme, see the
# documentation.
html_theme_options = {
  "header_links_before_dropdown": 6,
  "sidebarwidth": 200,
  "sticky_navigation": "false",
  "collapse_navigation": "false",
  "display_version": "true",
  "icon_links": [
    {
        "name": "GitHub",
        "url": urls['Repository'],
        "icon": "fa-brands fa-github",
    },
    ],
    "show_version_warning_banner": True,
    "footer_start": ["copyright"],
    "footer_center": ["sphinx-version"],
    "secondary_sidebar_items": {
        "**/*": ["page-toc", "edit-this-page", "sourcelink"],
        "examples/no-sidebar": [],
    },
    "use_edit_page_button": True,
  }
# Add any paths that contain custom static files (such as style sheets) here,
# relative to this directory. They are copied after the builtin static files,
# so a file named "default.css" will overwrite the builtin "default.css".
html_static_path = ['_static']
html_logo = "_static/openalea_web.svg"
html_favicon = "_static/openalea_web.svg"
# If false, no module index is generated.
html_domain_indices = True
# If false, no index is generated.
html_use_index = True
# If true, the index is split into individual pages for each letter.
html_split_index = False
# If true, links to the reST sources are added to the pages.
html_show_sourcelink = True
# If true, "Created using Sphinx" is shown in the HTML footer. Default is True.
html_show_sphinx = True
# If true, "(C) Copyright ..." is shown in the HTML footer. Default is True.
html_show_copyright = True
# Output file base name for HTML help builder.
htmlhelp_basename = project + '_documentation'
# Add infomation about github repository
html_context = {
    # "github_url": "https://github.com", # or your GitHub Enterprise site
    "github_user": "openalea",
    "github_repo": "my_pkg",
    "github_version": "main",
    "doc_path": "doc",
}

# -- Options for LaTeX output ---------------------------------------------
latex_elements = {
}
latex_documents = [
    (master_doc, 'pkg_name.tex', u'pkg_name Documentation',
     u'INRA / INRIA / CIRAD', 'manual'),
]

# -- Options for manual page output ---------------------------------------
# One entry per manual page. List of tuples
# (source start file, name, description, authors, manual section).
man_pages = [
    (master_doc, project, project + ' Documentation',
     [author], 1)
]

# -- Options for Texinfo output -------------------------------------------
# Grouping the document tree into Texinfo files. List of tuples
# (source start file, target name, title, author,
#  dir menu entry, description, category)
texinfo_documents = [
    (master_doc, project, project + ' Documentation',
     author, project, desc,
     'Miscellaneous'),
]
# Example configuration for intersphinx: refer to the Python standard library.
intersphinx_mapping = {'python': ('https://docs.python.org/', None)}
```

- `index.rst`: the main page of the documentation.

Also, the documentation should include notebook examples that illustrate the usage of the package. These notebooks should be stored in the `doc/notebooks` folder of the package.

## Testing

All packages should include tests to ensure that the code is working as expected. The tests should be stored in the `test` folder of the package, and should be written using the `pytest` framework.

Also, all notebooks in the `doc/notebooks` folder should be tested using the `nbmake` framework and be functional.

```python
pytest test
pytest --nbmake doc/notebooks
```
