===========
User Guide
===========

Models under OpenAlea are in the form of components that could be used as such, 
or combined together to build user-customised applications. OpenAlea provides two 
different ways to interacts with components:

* by visual programming, using Visualea
* by writing scripts, using a standard python development environment

Both methods allows you to save your application and run it routinely in batch mode. 
Visual programming is easier to start with, and it allows you to rapidly discover 
components of a package. Python scripting allows for programming more complex tasks, 
and provides an access to additional functionalities of models, by importing python 
modules that compose them.

Visual Programming
==================

OpenAlea provides an high level visual programming interface Visualea.

The main documentation is on
`Packages <https://openalea.readthedocs.io/en/latest/packages/index.html>`_ at Visualea.

Tutorials have been made on Visualea. You can find them on 
`Tutorials <https://openalea.readthedocs.io/en/latest/tutorials/index.html>`_.


Python Scripting
================

OpenAlea packages are available under the python scripting language. This allows to use the 
components of packages (as in visualea), but also to directly import python modules and get 
access to all functionalities documented in package's API.


Using Python
------------

Python is a scripting language widely spread in the scientific community. 
It has a lot of advantages :

* It is easy to learn, even for non programmers.
* It is an high level language, based on the object paradigm
* It is extensible with external libraries
* Multi-platform (Linux, Windows, Mac)

You can learn the basics with the `Official Tutorial <http://docs.python.org/tut/>`_

Python scripts could be launched by invoking python from a command line::

    python myScript.py

You can also launch a Python interpreter and run or test your script step by step.

The default interpreter could be launch by typing python in a terminal (Linux, Mac) or 
in a DOS windows. Under Windows, you may also use one of the following method:

* Use Start Menu -> openalea -> python shell
* You can use the default python interpreter GUI : IDLE (start menu -> Python 2.4 -> IDLE)

You can also use more ergonomic user interface, like ipython, that provides useful
functionalities (completion, coloration, execution of block of lines,…)


Importing OpenAlea Modules
--------------------------

The magic line which will make available all openalea modules is::

    import openalea

All OpenAlea modules are available in the openalea namespace. Refer to the modules documentation 
to learn how to use them.

You can also write simple python scripts in order to execute the same code several times.
