Installation
============

Conda Installation
------------------

`Conda <https://conda.io>`_ is a package manager that can be installed on Linux, Windows, and Mac.
If you have not yet installed conda on your computer, follow these instructions:

`Conda Download <https://conda.io/miniconda.html>`_. Use the Python 2.7 based installation.

OpenAlea Environment Installation
---------------------------------

Create an environment named *openalea*:
Launch a console (See Anaconda Prompt in Start menu on windows)

At first, if tou need all the OpenAlea environment, execute this::

    conda create -n openalea -c openalea boost=1.66

Let's say you need a package <*package_name*> in particuliar, you can execute this::

    conda create -n openalea -c openalea openalea.package_name boost=1.66

Here is an example if you want only *plantgl*, *lpy*, *mtg* and *caribu*::
    
    conda create -n openalea -c openalea openalea.plantgl openalea.lpy openalea.mtg alinea.caribu boost=1.66 

Activate the *openalea* environment::

    conda activate openalea

source should be written only on linux and macos.
Install the different packages
::

    conda install notebook=5.4 matplotlib pandas nbformat git

    conda install -c openalea -c conda-forge pvlib-python alinea.astk


