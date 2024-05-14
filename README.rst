.. openalea.rtfd.io:


======================
OpenAlea Documentation
======================

.. image:: https://readthedocs.org/projects/openalea/badge/?version=latest
   :target: https://openalea.readthedocs.io/en/latest/?badge=latest
   :alt: Documentation Status


Institutes
----------

OpenAlea is developped by 3 institutes : CIRAD, inria and INRAE.

License
-------
OpenAlea is licenced under the CeCILL-C free software license agreement.

Official documentation
----------------------
https://readthedocs.org/projects/openalea.readthedocs.io

Description
===========
OpenAlea is an open source project primarily aimed at the plant research community. It is a distributed collaborative effort to develop Python libraries and tools that address the needs of current and future works in Plant Architecture modeling. OpenAlea includes modules to analyse, visualize and model the functioning and growth of plant architecture. 

This repository contains all the documentation publish in the `official documentation of OpenAlea <https://readthedocs.org/projects/openalea.readthedocs.io/en/latest>`_.

Information about OpenAlea can also be found in the wiki: https://github.com/openalea/openalea.rtfd.io/wiki

Windows Installation
============

.. 1 - Install Micromamba (Package Manager)
The simplest way to install OpenaAlea and all its depencies is to use Miniforge 3:
`Install Miniforge 3 <https://github.com/conda-forge/miniforge>`_


.. 2 - Run Miniforge Prompt 
Once you have installed Miniforge, you will have access to Miniforge Prompt. 

Type this in your Miniforge Prompt:
    
    mamba create -n openalea -c openalea3 openalea.plantgl openalea.lpy openalea.visualea openalea.mtg notebook -y

    mamba activate openalea

Now you should be in your "openalea" environment ! Well Done !

Usage
=====
Tutorials to use the differents features of OpenAlea can be found in the `documentation <https://openalea.readthedocs.io/en/latest/tutorials/index.html>`_.

Sponsors
========
OpenAlea is mainly funded by three research institutes : CIRAD, INRAE and inria.

Contribution
============
You can contribute to the OpenAlea project by participating in the `Git Workflow <http://virtualplants.github.io/contribute/devel/git-workflow.html>`_, or by opening an issue or a pull request to adress a problem or a fix.
ss