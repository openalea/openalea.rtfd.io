======================
OpenAlea Documentation
======================

.. image:: https://readthedocs.org/projects/openalea/badge/?version=latest
   :target: https://openalea.readthedocs.io/en/latest/?badge=latest
   :alt: Documentation Status

Institutes (Sponsors)
---------------------

OpenAlea is developed, maintainted and mainly funded by three institutes: CIRAD, INRIA, and INRAE.

License
-------

OpenAlea is licensed under the CeCILL-C free software license agreement.

Official documentation
----------------------

https://readthedocs.org/projects/openalea.readthedocs.io

Description
===========

OpenAlea is an open source project primarily aimed at the plant research community. It is a distributed collaborative effort to develop Python libraries and tools that address the needs of current and future works in Plant Architecture modeling. OpenAlea includes modules to analyze, visualize, and model the functioning and growth of plant architecture.

This repository contains all the documentation published in the `official documentation of OpenAlea <https://readthedocs.org/projects/openalea.readthedocs.io/en/latest>`_.

Information about OpenAlea can also be found in the wiki: https://github.com/openalea/openalea.rtfd.io/wiki

Installation
============

Install Miniforge 3
===================

The simplest way to install OpenAlea and all its dependencies is to use Miniforge 3:
`Install Miniforge 3 <https://github.com/conda-forge/miniforge>`_

Create OpenAlea environment:
=============================

Once you have installed Miniforge, you will have access to Miniforge Prompt (Windows) or a terminal (Mac/Linux).

**Open Miniforge Prompt (Windows) or a terminal (Mac/Linux) and type:**

.. code-block:: bash

   mamba create -n openalea -c openalea3 openalea.plantgl openalea.lpy openalea.visualea openalea.mtg notebook -y

.. code-block:: bash

   mamba activate openalea

You should now be in your "openalea" environment! Well Done!

Usage
=====

Tutorials to use the different features of OpenAlea can be found in the `documentation <https://openalea.readthedocs.io/en/latest/tutorials/index.html>`_.

Contribution
============

You can contribute to the OpenAlea project by participating in the `Git Workflow <http://virtualplants.github.io/contribute/devel/git-workflow.html>`_, or by opening an issue or a pull request to address a problem or a fix.

Troubleshooting
===============

- **Common Issues**: List of common issues and solutions.

Common Issues
-------------

**Problem**: Installation fails with dependency errors.

**Solution**: Ensure that you are using the latest version of Miniforge and that your environment is clean before installing OpenAlea. You can remove an existing environment with:

.. code-block:: bash

   mamba env remove -n openalea

Then, try creating the environment again.

**Problem**: "mamba" command not found.

**Solution**: Make sure Miniforge is correctly installed and added to your system's PATH. You might need to restart your terminal or Miniforge Prompt.

**Problem**: OpenAlea modules not found when importing in a Jupyter notebook.

**Solution**: Ensure that you have activated the OpenAlea environment before starting the Jupyter notebook. You can activate the environment with:

.. code-block:: bash

   mamba activate openalea

If the issue persists, try installing the Jupyter notebook within the OpenAlea environment:

.. code-block:: bash

   mamba install notebook


- **FAQs**: Frequently asked questions and answers.

**Question**: How do I update OpenAlea to the latest version?

**Answer**: To update OpenAlea and its dependencies, activate your OpenAlea environment and run:

.. code-block:: bash

   mamba update -c openalea3 openalea.plantgl openalea.lpy openalea.visualea openalea.mtg

**Question**: How do I contribute to the OpenAlea project?

**Answer**: You can contribute by participating in the `Git Workflow <http://virtualplants.github.io/contribute/devel/git-workflow.html>`_, or by opening an issue or a pull request on the OpenAlea GitHub repository.

**Question**: Where can I find more tutorials and examples?

**Answer**: More tutorials and examples can be found in the `official documentation <https://openalea.readthedocs.io/en/latest/tutorials/index.html>`_.



Contact
=======

For further assistance, you can reach out to the development team creating an `issue on github <https://github.com/openalea/openalea/issues>`_.
