# OpenAlea devlopment guidelines

> [!IMPORTANT]
>
> ___Definition___: Coding rules, or good practices, or coding conventions, aiming at  uniforming source code in a project.

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

Within OpenAlea, we have defined a set of minimal and limited guidelines that are mandatory for all developers.

These guidelines are used to ensure the quality of the code and to facilitate the deployment and diffusion of the software, but also to help global OpenAlea support and maintenance.
Same guidelines should be applied to all OpenAlea projects and are detailed below.

Although OpenAlea guidelines are limited to ensure that scientific developers can easily contribute to the project, we encourage developers to follow more general guidelines. Very good examples can be found in:

- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html) : set of rules for writing clear and readable Python code used at Google.
- [Python package guide](https://www.pyopensci.org/python-package-guide/index.html) : guide for developing Python packages for open science. Best practices and recommandations for developing Python packages.
- [Packaging Python](https://packaging.python.org/en/latest/) : collection of tutorials and references to help you distribute and install Python packages with modern tools.
- [Learn Scientific Python](https://learn.scientific-python.org/development/) : guide for writting maintainable, reusable, and shareable Python package for scientific computing.

## Package layout and namespace

- All [OpenAlea](https://github.com/openalea) and [OpenAlea-incubator](https://github.com/openalea-incubator) projects should use 'openalea' as a global namespace, to manifest their belonging to openalea initiative. Importing an openalea package will therefore always look like:

```python
from openalea.pkg_name import module_name
```

- Also, we recommand to use the [src-layout](https://setuptools.pypa.io/en/latest/userguide/package_discovery.html#src-layout) for the source code of the project.
  That yield the following basic layout for your package: 

```bash
pkg_name
├── CHANGELOG.md               ┐
├── CODE_OF_CONDUCT.md         │
├── CONTRIBUTING.md            │
├── README.md                  |
├── doc                        │ Package documentation
│   └── index.md               │
│   └── ...                    ┘
│   └── examples               ┐
│   └──── notebook1.ipynb      │ Package examples
│   └──── ...                  ┘
├── LICENSE                    ┐ Package metadata and build configuration
├── pyproject.toml             ┘ 
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
  - License: [![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
  - Version of the package on Anaconda: [![Anaconda-Server Badge](https://anaconda.org/openalea3/mtg/badges/version.svg)](https://anaconda.org/openalea3/mtg)
- installation instructions: how to install the package using `conda` or `pip`.
- usage instructions: how to use the package, with a brief and simple example.
- links to the documentation, the license, the code of conduct, the contributing guidelines, and the changelog.
- Citation information: how to cite the package in a scientific publication.

### LICENSE

This file should include the license of the project. Most common licenses used in open source projects are:

- the [MIT License](https://choosealicense.com/licenses/mit/) : a permissive license that is short and to the point. It lets people do anything they want with the code as long as they provide attribution back to the original author and don’t hold the author liable.
- the [CNU GPLv3 License](https://choosealicense.com/licenses/gpl-3.0/) : a copyleft license that requires anyone who distributes the code or a derivative work to make the source available under the same terms. It is often used for libraries and applications that are intended to be shared and improved by the community.

Other options are available, and you can use the [Choose a License](https://choosealicense.com/) website to help you choose the right license for your project.

### CONTRIBUTING.md

This file shoud include information on how to contribute to the project: how to report bugs, how to request new features, how to ask questions and how to submit code changes.

### CODE_OF_CONDUCT.md

This document will help building a community around your package. It sets what you expect from the users and contributors of the project, in terms of behavior and communication. You can check examples on the web, such as [scikit-learn](https://github.com/scikit-learn/scikit-learn/blob/main/CODE_OF_CONDUCT.md).

### CHANGELOG.md

This file should be a ressource for developers anf users to know what has changed in the project over time. It should include a list of changes for each version of the project.

## pyproject.toml

OpenAlea projects should use the `pyproject.toml` file to define the build configuration and the metadata of the project.
This file should contain the following sections:

- Use [`setuptools` as the build system](https://setuptools.pypa.io/en/latest/). `setuptools` is the most widely used build system for Python packages. It is used to define the metadata of the package, the dependencies, and the entry points.

```toml
[build-system]
requires = ["setuptools>=61", "setuptools_scm[toml]>=7"]
build-backend = "setuptools.build_meta"

[tool.setuptools_scm]
write_to = "src/openalea/pkg_name/_version.py"
```

If your package needs an extension module, you should check the [dedicated `setuptools` documentation](https://setuptools.pypa.io/en/latest/userguide/ext_modules.html#building-extension-modules)

- Define the metadata of the project in the `[project]` section.
This metadata should include the name of the project, the authors, the description, the README file, the license file, the Python version required, the classifiers, the dynamic metadata, and the dependencies.

```toml
[project]
name = "openalea.pkg_name"
authors = [
  { name = "Jane Doe", email = "jane.doe@mail.com" },
  ...
]
description = "FSPM tools for OpenAlea"
readme = "README.md"
license.file = "LICENSE"
requires-python = ">=3.10"
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
]
dynamic = ["version"]
dependencies = [
    "openalea.deploy",
    "openalea.plantgl",
    "numpy >= 1.24",
    ...
]
```

- Additionaly you can define the optional dependencies for development mode and test mode in the [`[project.optional-dependencies]` section](https://setuptools.pypa.io/en/latest/userguide/dependency_management.html#optional-dependencies).

```toml
[project.optional-dependencies]
test = [
  "pytest >=6",
  "pytest-cov >=3",
  ...
]
dev = [
  "pytest >=6",
  "pytest-cov >=3",
]
docs = [
  "sphinx>=7.0",
  "myst_parser>=0.13",
  "sphinx_copybutton",
  "sphinx_autodoc_typehints",
  ...
]
```

- Define the URLs of the project in the `[project.urls]` section.

```toml
[project.urls]
Homepage = "https://github.com/openalea/pkg_name"
"Bug Tracker" = "https://github.com/openalea/pkg_name/issues"
Discussions = "https://github.com/openalea/pkg_name/discussions"
Changelog = "https://github.com/openalea/pkg_name/releases"
```

## Data files

You might want to include data files in your package, wether you need it to test your package, or allows user to run tutorials without downloading the sources via git. For most cases, we recomend hosting the data directly in the pkg source directory. However, if the size of data files becomes large (eg for realistic images or databases) they will bloat your source directory and slow down the installation and/or CI workflow. In such cases, we recommend storing you data on public spaces (github or xenodo), and provide an access in a dedicated module using [Pooch](https://www.fatiando.org/pooch).Both approaches are detailed below.

### Distributing data with the package sources

This approach is detailed in [`setuptools` documentation](https://setuptools.pypa.io/en/latest/userguide/datafiles.html#accessing-data-files-at-runtime). This approach should be prefered to a direct manipulation of the package’s \_\_file\_\_ attribute, as the later can fail if your data are ditributed via zip, egg or wheels. 

The recommended way of organising your data is to add a data folder in your package source folder, and add a generic MANIFEST.in file at the root of the package:

```bash
pkg_name
├── ...
├── MANIFEST.in                  ] declaration of package data
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

MANIFEST.in should declare what files are to be included. It could be as simple and generic as :

```bash
recursive-include src/openalea/pkg_name/data *
```

Using this layout, no further modification should be brought to your package, provided you are using a toml file.
If you are using a setup.py file, you should manualy set include-package-data option to true and use find_namespace_package to scan src.

You can then access data using importlib.ressources. It is currently recommended to use `importlib_resources` backport module for Python 3.7 and above, as importlib.resources only works for python 3.10 and above. The only diffference is to replace the underscore by a point in the following examples.: 

```python
from importlib_resources import files, path

datadir = 'openalea/pkg_name/data'
# return the list of files present in the data dir:
data = list(files(datadir).iterdir())

# return the content of the ressource named 'data_fileA.csv':
data1 = (files(datadir) / 'data_fileA.csv').read_text()

# read the content using pandas read_csv reader
import pandas
with path(datadir) / 'data_fileA.csv' as p:
   data1 = pandas.read_csv(p)
```

### Openalea alternative: using openalea.deploy.shared_data approach

This approach is working for openalea packages relying of setup.py, as openalea currently warrants unzipped source code distribution in this case. However, the above method should now be prefered, as this constraint can be released in the future.

In this case your layout will look like:

```bash
pkg_name
├── ...
|── share/data                   ┐
|       ├── __init__.py          │ Data files
|       ├── data_fileA.csv       |
|       └── data_fileB.csv       ┘
├── src                          ┐
│   └── openalea/pkg_name        │
│       ├── __init__.py          │ Package source code
│       ├── moduleA.py           │
│       └── moduleB.py           ┘
```

You can then access the data files at runtime using [`openalea.deploy`](https://github.com/openalea/deploy).:

```python
from openalea.deploy.shared_data import shared_data
import openalea.pkg_name

data_dir = shared_data(openalea.pkg_name)
```

and then access the data files using the `data_dir` '/' method.

One example can be found in [`openalea.rose` package](https://github.com/openalea-incubator/rose/blob/paper/src/openalea/rose/data.py)

### Large data files

Large data files should not be included in the package, so as to keep your repository lightweight and functional. Instead, they should be stored in a separate place and be accessed via [Pooch](https://www.fatiando.org/pooch).

We don't have any example in OpenAlea yet, but we plan to follow a similar strategy as the one used for [x-array data](https://github.com/pydata/xarray-data)

## Building the package

The package should be installable using the the [`conda` package manager](https://docs.conda.io/projects/conda/en/latest/index.html) and `conda / mamba` commands, from the [`openalea3` conda channel](https://anaconda.org/openalea3), e.g.:

```bash
mamba install -c openalea3 -c conda-forge openalea.pkg_name openalea.plantgl numpy
```

> [!NOTE]
> We strongly recommend to use `mamba` instead of `conda` as it much faster and less error prone to versions conflicts.

Implications are that:

- all dependances should also be available from a conda channel or via `pip`.
- package should be built and uploaded to the `openalea3` conda channel. A [dedicated CI/CD pipeline](#ci-cd) can be used for this purpose.
- no `git clone + pip install .` should be required to install the package. However, it is still possible to install the package from the source code and use the `pip` develop mode with the `pip install -e .` command.

## CI-CD

CI/CD stands for Continuous Integration / Continuous Deployment. It is a set of practices and tools that allow to automate the building, testing, and deployment of the software.
It is a key practice for ensuring the quality of the software and the reliability of the deployment process.

Within the OpenAlea community, we use a custom made [GitHub Actions](https://github.com/openalea/github-action-conda-build) to build and deploy the packages to the `openalea3` conda channel.

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

This action will build the package on a matrix of operating systems (`[ubuntu-latest , macos-latest , windows-latest]`) and Python versions (`[3.8, 3.9, 3.10, 3.11, 3.12]`) every time a new commit is pushed to the repository.

Also, it will deploy the package to the `openalea3` conda channel every time a new tag starting with `v` (typicaly when you tag a new version of the package, like `v.1.0.0`) is pushed to the repository. This means that the developer needs to explicitely tag the version of the package to deploy it.

## Documentation

The documentation of the package should be written using the [Sphinx](https://www.sphinx-doc.org/en/master/) documentation generator and hosted on the [ReadTheDocs](https://readthedocs.org/) platform.

To setup the ReadTheDocs documentation, you need to add a `.readthedocs.yml` file to the root of your project with the following content:

```yaml
version: 2

build:
  os: "ubuntu-22.04"
  tools:
    python: "mambaforge-22.9"

conda:
  environment: doc/environment.yml
```

This file will tell ReadTheDocs to build the documentation using the environment describe in the the `doc/environment.yml` file and to setup the environment using `mambaforge`.

The documentation should be written in the `doc` folder of the package and should contain the following files:

- `conf.py`: the configuration file of the documentation, and how to build it. e.g.:

```python
# -*- coding: utf-8 -*-
import sys
import os

import pydata_sphinx_theme # Pydata theme: https://pydata-sphinx-theme.readthedocs.io/en/stable/index.html

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
    'sphinx.ext.imgmath',   # support for math equations
    'sphinx.ext.ifconfig',  # support for conditional content
    'sphinx.ext.viewcode',  # support for links to source code
    'sphinx.ext.coverage',  # includes doc coverage stats in the documentation
    'sphinx.ext.todo',      # support for todo items
    'sphinx.ext.napoleon',  # support for numpy and google style docstrings
    "sphinx_favicon",      # support for favicon
    "nbsphinx",     # for integrating jupyter notebooks
    "myst_parser"   # for parsing .md files
]
# Add any paths that contain templates here, relative to this directory.
templates_path = ['_templates']
autosummary_generate = True
exclude_patterns = ['_build', '_templates']
# The suffix(es) of source filenames.
# You can specify multiple suffix as a list of string:
source_suffix = {
    '.rst': 'restructuredtext',
    '.md': 'markdown',
}
# The master toctree document.
master_doc = 'index'
# General information about the project.
project = u'pkg_name'
copyright = u'Cecill-C INRAE / INRIA / CIRAD'
author = u'Jane Doe et al.'
# The version info for the project you're documenting, acts as replacement for
# |version| and |release|, also used in various other places throughout the
# built documents.
#
# The short X.Y version.
version = u'x.x'
# The full version, including alpha/beta/rc tags.
release = u'x.x.x'
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
  "display_version": "true"
  "icon_links": [
    {
        "name": "GitHub",
        "url": "https://github.com/openalea/openalea.rtfd.io",
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
htmlhelp_basename = 'pkg_name_documentation'

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
    (master_doc, 'pkg_name', u'pkg_name Documentation',
     [author], 1)
]

# -- Options for Texinfo output -------------------------------------------
# Grouping the document tree into Texinfo files. List of tuples
# (source start file, target name, title, author,
#  dir menu entry, description, category)
texinfo_documents = [
    (master_doc, 'pkg_name', u'pkg_name Documentation',
     author, 'pkg_name', 'One line description of project.',
     'Miscellaneous'),
]
# Example configuration for intersphinx: refer to the Python standard library.
intersphinx_mapping = {'python': ('https://docs.python.org/', None)}
```

- `index.rst`: the main page of the documentation.

Also, the documentation should include notebook examples that illustrate the usage of the package. These notebooks should be stored in the `doc/notebooks` folder of the package.

## Testing

All packages should include tests to ensure that the code is working as expected. The tests should be stored in the `tests` folder of the package, and should be written using the `pytest` framework.

Also, all notebooks in the `doc/notebooks` folder should be tested using the `nbsphinx` framework and be functional.
