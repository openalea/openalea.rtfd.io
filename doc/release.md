# Release 2025 notes

## Openalea Improvements

- New Guidelines have been published [guide lines](./development/guidelines.md) for all the OpenAlea packages
  - namespace is now consistently set to `openalea/pkg_name` (`alinea/pkg_name` is kept for compatibility but is no longer recommanded)
  - conda packaging:
    - New Mac OS X architecture (M1, ...): support osx-arm64 on top of osx-64 architecture
    - all packages have a `conda` directory with `meta.yaml` using metadata from `pyproject.toml` for conda packaging and a `environment.yml` file
    - `environment.yml` is used to build documentation and also to install locally package in development mode
      ```bash
      mamba env create -f conda/environment.yml
      ```
    - continuous integration:
      - consistent continuous integration / deployment as been set up for all packages using a [dedicated github-action workflow](github.com/openalea/action-build-publish-anaconda)
      - all packages are now automatically uploaded to [openalea3 conda channel](https://anaconda.org/openalea3/repo)
    - installation via conda is now for all packages in the release:
      ```bash
      mamba install openalea.pkg_name -c openalea3
      ```
  - all packages but `openalea.plantgl` are locally pip installable
      - `setup.py` is replaced by `pyproject.toml`
      - package can be installed by running `pip install .` or in editable mode `pip install -e .` in root directory of the project
      - `openalea.ratp` is not working in editable mode
  - all packages have API reference documentation and tutorials that are still an ongoing work for some packages

## Packages change log
The foolowing packages are part of the release:

    openalea.plantgl 
    openalea.lpy 
    openalea.core 
    openalea.mtg 
    openalea.widgets 
    openalea.scipack 
    openalea.grapheditor
    openalea.oalab 
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

Main changes, GitHub and documentation link are listed for each packages below. 

### openalea.plantgl 3.22.3
- [https://github.com/openalea/plantgl](https://github.com/openalea/plantgl)
- Documentation: [https://plantgl.rtfd.io](https://plantgl.rtfd.io)
- OpenAlea.PlantGL provides light interception methods comparable to [openalea.caribu](https://caribu.readthedocs.io) 
- support c++17 and numpy 2

### openalea.lpy 3.15.4
- [https://github.com/openalea/lpy](https://github.com/openalea/lpy)
- Documentation: [https://lpy.readthedocs.io](https://lpy.readthedocs.io)
- OpenAlea.L-Py is a simulation software that mixes L-systems construction with the Python high-level modeling language.
- support c++17 and numpy 2

### openalea.core 2.5.0
- [https://github.com/openalea/core](https://github.com/openalea/core)
- OpenAlea.Core implements the components and workflows execution

### openalea.mtg 2.3.0
- [https://github.com/openalea/mtg](https://github.com/openalea/mtg)
- Documentation: [https://mtg.rtfd.io](https://mtg.rtfd.io)
- Visualisation of MTG in the Notebook is provided by the package openalea.widgets

### openalea.widgets 1.1.2
- [https://github.com/openalea/oawidgets](https://github.com/openalea/oawidgets)
- Documentation: [https://oawidgets.readthedocs.io](https://oawidgets.readthedocs.io)
- Set of jupyter notebook widgets dedicated to OpenAlea.
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

### openalea.scipack 2.5.2
- [https://github.com/openalea/scipack](https://github.com/openalea/scipack)
- Documentation: [https://scipack.readthedocs.io](https://scipack.readthedocs.io)
- `openalea.scipack` replaces the meta-package `openalea.components` a set of wrappers of standard Python packages for `openalea.visualea`
- It regroups: `openalea.stdlib`, `openalea.pylab`, `openalea.numpy` and `openalea.image`, but calls did not change.

### openalea.grapheditor 2.5.0
- [https://github.com/openalea/grapheditor](https://github.com/openalea/grapheditor)
- Documentation: [https://grapheditor.readthedocs.io](https://grapheditor.readthedocs.io)
- OpenAlea.GraphEditor is a base package for editing graph with various graph data structures.
- This package is used by `openalea.visualea`

### openalea.oalab 2.5.0
- [https://github.com/openalea/oalab](https://github.com/openalea/oalab)
- OpenAlea.OaLab is another end user application.

### openalea.visualea 2.5.0
- [https://github.com/openalea/visualea](https://github.com/openalea/visualea)
- Documentation: [https://visualea.readthedocs.io](https://visualea.readthedocs.io)
- OpenAlea.VisuAlea has been resurrected
- All the workflows are not fully functional but the software is functional

### openalea.weberpenn 2.5.0
- [https://github.com/openalea/weberpenn](https://github.com/openalea/weberpenn)
- OpenAlea.WeberPenn is a simple model to build trees from parameters.
- The model is available through VisuAlea

### openalea.rsml 1.5.0
- [https://github.com/openalea/rsml](https://github.com/openalea/rsml)
- Documentation: [https://rsml.readthedocs.io](https://rsml.readthedocs.io)
- OpenAlea package managing the [RootSystemML](http://rootsystemml.github.io/) file format that represents root architectural data
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

### openalea.caribu 8.2.1
- [https://github.com/openalea/caribu](https://github.com/openalea/caribu)
- Documentation: [https://caribu.readthedocs.io](https://caribu.readthedocs.io)
- Caribu is a modelling suite for lighting 3D virtual scenes, especially designed for the illumination of virtual plant canopies such as virtual crop fields.
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

### openalea.astk 3.1.0
- [https://github.com/openalea/astk](https://github.com/openalea/astk)
- Documentation: [https://openalea-astk.readthedocs.io](https://openalea-astk.readthedocs.io)
- Astk allows to calculate sky luminance and sky sources to be used with FSPM light models from weather data.
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

### openalea.adel 2.1.1
- [https://github.com/openalea/adel/](https://github.com/openalea/adel/)
- Documentation: [https://adel.readthedocs.io](https://adel.readthedocs.io)
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

### openalea.ratp 2.2.0
- [https://github.com/openalea/pyratp](https://github.com/openalea/pyratp)
- Documentation: [https://pyratp.rtfd.io](https://pyratp.rtfd.io)
- RATP: Radiation Absorption, Transpiration and Photosynthesis.
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

### openalea.spice 1.1.0
- [https://github.com/openalea/spice](https://github.com/openalea/spice)
- Documentation: [https://openalea-spice.readthedocs.io](https://openalea-spice.readthedocs.io)
- Spice (Spectral Photon Interception in Controlled Environment) : New package for light simulation in controlled environments based on photon mapping.

### openalea.hydroroot 2.1.0
- [https://github.com/openalea/hydroroot](https://github.com/openalea/hydroroot)
- Documentation: [https://hydroroot.readthedocs.io](https://hydroroot.readthedocs.io)
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

### openalea.hydroshoot 5.3.0
- [https://github.com/openalea/hydroshoot](https://github.com/openalea/hydroshoot)
- Documentation: [https://hydroshoot.readthedocs.io](https://hydroshoot.readthedocs.io)
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
- [https://github.com/openalea/WheatFspm](https://github.com/openalea/WheatFspm)
- Documentation: [https://wheatfspm.readthedocs.io](https://wheatfspm.readthedocs.io)
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

### openalea.phenomenal 1.10.4
- [https://github.com/openalea/phenomenal](https://github.com/openalea/phenomenal)
- Documentation: [https://phenomenal.readthedocs.io](https://phenomenal.readthedocs.io)
- An automatic open source library for 3D shoot architecture reconstruction and analysis for image-based plant phenotyping
- optional package [openalea.phenotyping_data](https://github.com/openalea/phenotyping_data) provides Data from plant phenotyping platform primarly aimed at desmonstrating/testing openalea.phenomenal, needed to run some of the tutorials
- Calibration has been extented to n-cameras n-calibration targets cases, and with simpler parameterisation
