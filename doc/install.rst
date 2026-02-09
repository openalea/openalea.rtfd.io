Installation
============

Conda Installation
------------------

`Conda <https://conda.io>`_ is a package manager that can be installed on Linux, Windows, and Mac.
If you have not yet installed conda on your computer, we recommand to install `miniforge <https://github.com/conda-forge/miniforge>`_, you can find instructions and installers in the previous page or in `conda-forge.org <https://conda-forge.org/download/>`_.

OpenAlea Installation
---------------------

The *recommended* way to install OpenAlea is to create a new conda environment.

First, create an environment named *openalea*:

Launch a console or a terminal (See Miniforge Prompt in Start menu on windows).
In this console, to install a given openalea package <*package_name*> with its dependencies, execute this::

    mamba create -n openalea -c openalea3 -c conda-forge openalea.<*package_name*>

Here is an example if you want only *PlantGL*, *lpy*, *MTG* and *Caribu*::

    mamba create -n openalea -c openalea3 -c conda-forge openalea.plantgl openalea.lpy openalea.mtg openalea.caribu

Activate the *openalea* environment::

    mamba activate openalea

In this environment, you may also want to install other Scientific Python packages::

    mamba install jupyterlab matplotlib pandas

In the documentation of each package, a installation procedure is described.

Updating OpenAlea
-----------------

How to Update OpenAlea
~~~~~~~~~~~~~~~~~~~~~~

To update OpenAlea and its dependencies, activate your OpenAlea environment and run::

    mamba update -c openalea3 openalea.plantgl openalea.lpy openalea.visualea openalea.mtg


|
Troubleshooting
===============

Installation Issues
-------------------

Dependency Errors
~~~~~~~~~~~~~~~~~

Description Installation fails with dependency errors.

**Solution**: Ensure that you are using the latest version of Miniforge and that your environment is clean before installing OpenAlea. You can remove an existing environment with::

   mamba env remove -n openalea

Then, try creating the environment again.

Command Not Found
~~~~~~~~~~~~~~~~~

**Description**: "mamba" command not found.

**Solution**: Make sure Miniforge is correctly installed and added to your system's PATH. You might need to restart your terminal or Miniforge Prompt.

Module Import Issues
--------------------

Modules Not Found in Jupyter Notebook
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Description**: OpenAlea modules not found when importing in a Jupyter notebook.

**Solution**: Ensure that you have activated the OpenAlea environment before starting the Jupyter notebook. You can activate the environment with::

   mamba activate openalea

If the issue persists, try installing the Jupyter notebook within the OpenAlea environment::

   mamba install notebook
