# Release change log

## Openalea general change log

- All packages follow [guide lines](./development/guidelines.md)
  - namespace is `openalea/pkg_name`
  - all packages are pip installable
      - `setup.py` is now replaced by `pyproject.toml`
      - package can be installed by running `pip install .` or in editable mode `pip install -e .` in root directory of the project
  - conda:
    - all packages have a `conda` directory with `meta.yaml` using metadata from `pyproject.toml` for conda packaging and a `environment.yml` file
    - `environment.yml` is used to build documentation and also to install locally package in development mode
    ```bash
    mamba env create -f conda/environment.yml
    ```
    - installation via conda is now for all packages in the release: `mamba install openalea.pkg_name -c openalea3`

## Packages change log

### PyQGLViewer

### openalea.plantgl

### openalea.lpy

### openalea.mtg

### openalea.widgets
- namespace changed from `oawidgets` to `openalea.widgets`
  instead of
```python
import oawidgets
from oawidgets import *
```
do
```python
import openalea.widgets
from openalea.widgets import *
```

### openalea.astk
- namespace changed from `alinea.astk` to `openalea.astk`
  instead of
```python
import alinea.astk
from alinea.astk.Weather import Weather
```
do
```python
import openalea.astk
from openalea.astk.Weather import Weather
```

### openalea.ratp
- namespace changed from `alinea.pyratp` to `openalea.ratp`
  instead of
```python
import alinea.pyratp
from alinea.pyratp.skyvault import Skyvault
```
do
```python
import openalea.ratp
from openalea.ratp.skyvault import Skyvault
```

### openalea.caribu
- Caribu has been split in two packages: `openalea.caribu` pure python and `openalea.libcaribu` with c++ code.
- namespace changed from `alinea.caribu` to `openalea.caribu`
  instead of
```python
import alinea.caribu
from alinea.caribu.caribu import radiosity
```
do
```python
import openalea.caribu
from openalea.caribu.caribu import radiosity
```

### openalea.visualea

### openalea.core

### openalea.scipack
- `openalea.scipack` replaces the meta-package `openalea.components` a set of wrappers of standard Python packages for `openalea.visualea`
- It regroups: `openalea.stdlib`, `openalea.pylab`, `openalea.numpy` and `openalea.image`, but calls did not change.

### openalea.grapheditor

### openalea.oalab

### openalea.weberpenn
