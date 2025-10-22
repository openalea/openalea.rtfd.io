Installation
============

Conda Installation
------------------

`Conda <https://conda.io>`_ is a package manager that can be installed on Linux, Windows, and Mac.
If you have not yet installed conda on your computer, follow these instructions : `Conda Installation <https://conda.io/miniconda.html>`_.

.. warning::
    `mamba <https://mamba.readthedocs.io/en/latest/installation/mamba-installation.html>`_ is a fast and reliable alternative to *conda*. We highly recommend using *mamba* instead of *conda*.

OpenAlea Installation
---------------------------------

The *recommended* way to install OpenAlea is to create a new conda environment.

First, create an environment named *openalea*:

Launch a console or a terminal (See Anaconda Prompt in Start menu on windows).
In this console, to install a given openalea package <*package_name*> with its dependencies, execute this::

    mamba create -n openalea -c openalea3 -c conda-forge openalea.<*package_name*>

Here is an example if you want only *PlantGL*, *lpy*, *MTG* and *Caribu*::

    mamba create -n openalea -c openalea3 -c conda-forge openalea.plantgl openalea.lpy openalea.mtg openalea.caribu

Activate the *openalea* environment::

    mamba activate openalea

In this environment, you may also want to install other Scientific Python packages::

    mamba install notebook matplotlib pandas

In the documentation of each package, a installation procedure is described.
