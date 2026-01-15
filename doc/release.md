# Release 2025 notes

## Openalea general change log

- All packages follow [guide lines](./development/guidelines.md)
  - namespace is now consistently set to `openalea/pkg_name` (`alinea/pkg_name` is kept for compatibility but is no longer recommanded)
  - conda:
    - support osx-arm64 on top of osx-64 architecture
    - all packages have a `conda` directory with `meta.yaml` using metadata from `pyproject.toml` for conda packaging and a `environment.yml` file
    - `environment.yml` is used to build documentation and also to install locally package in development mode
      ```bash
      mamba env create -f conda/environment.yml
      ```
    - continuous integration:
      - consistent continuous integration / deployment as been set up for all packages using a [dedicated github-action workflow](github.com/openalea/action-build-publish-anaconda)
      - all packages are now automatically uploaded to [openalea3 conda channel](https://anaconda.org/openalea3/repo)
    - installation via conda is now for all packages in the release: `mamba install openalea.pkg_name -c openalea3`
  - all packages but `openalea.plantgl` are pip installable
      - `setup.py` is now replaced by `pyproject.toml`
      - package can be installed by running `pip install .` or in editable mode `pip install -e .` in root directory of the project
      - `openalea.ratp` is not working in editable mode
  - all packages have API reference documentation and tutorials, this is still an ongoing work for some package

## Packages change log
The foolowing packages are part of the release:

    openalea.plantgl
    openalea.lpy
    openalea.core
    openalea.widgets
    openalea.mtg
    openalea.scipack
    openalea.oalab
    openalea.grapheditor
    openalea.visualea
    openalea.weberpenn
    openalea.rsml
    openalea.caribu
    openalea.astk
    openalea.adel
    openalea.spice
    openalea.hydroroot
    openalea.phenomenal
    openalea.hydroshoot
    openalea.wheatfspm
    openalea.ratp

### openalea.plantgl
- Documentation: https://plantgl.rtfd.io
- OpenAlea.PlantGL provides light interception methods comparable to [openalea.caribu](https://caribu.readthedocs.io) 
- support c++17 and numpy 2

### openalea.lpy
- Documentation: https://lpy.readthedocs.io
- support c++17 and numpy 2

### openalea.core
- OpenAlea.Core implements the components and workflows execution

### openalea.mtg
- Documentation: https://mtg.rtfd.io
- Visualisation of MTG in the Notebook is provided by the package openalea.widgets

### openalea.widgets
- Documentation: https://oawidgets.readthedocs.io
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

### openalea.scipack
- Documentation: https://scipack.readthedocs.io
- `openalea.scipack` replaces the meta-package `openalea.components` a set of wrappers of standard Python packages for `openalea.visualea`
- It regroups: `openalea.stdlib`, `openalea.pylab`, `openalea.numpy` and `openalea.image`, but calls did not change.

### openalea.grapheditor
- Documentation: https://grapheditor.readthedocs.io
- OpenAlea.GraphEditor is a base package for editing graph with various graph data structures.
- This package is used by `openalea.visualea`

### openalea.oalab
- OpenAlea.OaLab is another end user application.

### openalea.visualea
- Documentation: https://visualea.readthedocs.io
- OpenAlea.VisuAlea has been resurrected
- All the workflows are not fully functional but the software is functional

### openalea.weberpenn
- OpenAlea.WeberPenn is a simple model to build trees from parameters.
- The model is available through VisuAlea

### openalea.rsml
- Documentation: https://rsml.readthedocs.io
- OpenAlea package managing the RootSystemML file format that represents root architectural data http://rootsystemml.github.io/
- namespace changed from `rsml` to `openalea.rsml`
  instead of
```python
import rsml
from rsml import *
```
do
```python
import openalea.rsml
from openalea.rsml import *
```

### openalea.caribu
- Documentation: https://caribu.readthedocs.io
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

### openalea.astk
- Documentation: https://openalea-astk.readthedocs.io
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

### openalea.adel
- Documentation: https://adel.readthedocs.io
- OpenAlea.Adel (Architectural model of DEvelopment based on L-systems) allows to simulate the 3D architectural development of the shoot of gramineaous plant.
- namespace changed from `alinea.adel` to `openalea.adel`
  instead of
```python
import alinea.adel
from alinea.adel import *
```
do
```python
import openalea.adel
from openalea.adel import *
```

### openalea.ratp
- Documentation: https://pyratp.rtfd.io
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

### openalea.spice
- Documentation: https://openalea-spice.readthedocs.io
- New package that provides minimal but extensible header only implementation of photon mapping in C++

### openalea.hydroroot
- Documentation: https://hydroroot.readthedocs.io
- OpenAlea.HydroRoot is a hydraulic root architecture modelling and a root architecture system generator package
- namespace changed from `hydroroot` to `openalea.hydroroot`
  instead of
```python
import hydroroot
from hydroroot import *
```
do
```python
import openalea.hydroroot
from openalea.hydroroot import *
```

### openalea.hydroshoot
- Documentation: https://hydroshoot.readthedocs.io
- Hydroshoot provides a grapevine-specific module (architecture) which builds plant shoot structure for potted of trained grapevines
- namespace changed from `hydroshoot` to `openalea.hydroshoot`
  instead of
```python
import hydroshoot
from hydroshoot import *
```
do
```python
import openalea.hydroshoot
from openalea.hydroshoot import *
```

### openalea.wheatfspm
- Documentation: https://wheatfspm.readthedocs.io
- WheatFspm is a Functional Structural Plant Model (FSPM) of wheat which fully integrates shoot morphogenesis and the metabolism of carbon (C) and nitrogen (N) at organ scale within a 3D representation of plant architecture. 
- It now regroups in one model: CN-Wheat, Elong-Wheat, fspm-wheat, Growth-Wheat, Farquhar-Wheat, Respi-Wheat, Senesc-Wheat
- namespace changed from `fspmwheat` to `openalea.fspmwheat`, idem for cnwheat, elongwheat, farquharwheat, growthwheat, respiwheat, senescwheat
  instead of
```python
from fspmwheat import *
from cnwheat import *
from elongwheat import *
from farquharwheat import *
from growthwheat import *
from respiwheat import *
from senescwheat import *
```
do
```python
from openalea.fspmwheat import *
from openalea.cnwheat import *
from openalea.elongwheat import *
from openalea.farquharwheat import *
from openalea.growthwheat import *
from openalea.respiwheat import *
from openalea.senescwheat import *
```

### openalea.phenomenal
- Documentation: https://phenomenal.readthedocs.io
- An automatic open source library for 3D shoot architecture reconstruction and analysis for image-based plant phenotyping
- optional package [openalea.phenotyping_data](https://github.com/openalea/phenotyping_data) provides Data from plant phenotyping platform primarly aimed at desmonstrating/testing openalea.phenomenal, needed to run some of the tutorials
