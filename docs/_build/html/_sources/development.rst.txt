Development
===========

This document describes the OpenAlea framework from the developer's point of view, 
characterizing how to make OpenAlea package easily available to the community.


An introduction to OpenAlea
---------------------------

Why adapt your tool for OpenAea ?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Developing your package in the openalea framework present a number of benefits. It allows

* your library to be shared with the community (do not reinvent the wheel).
* easy comparisons of different models.
* cooperation (the outputs can be directly reused in an other model).
* visibility of your work.


What OpenAlea provides for developers ?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
OpenAlea provides some tools to facilitate package creation and to share code.

Read the build and install framework document.


Contribute to OpenAlea
----------------------

Feel free to report a bug or suggest new features
on public `OpenAlea Github <https://github.com/openalea>`_.

You can also develop your own package as described in next section.


Develop your own package
------------------------

What is an OpenAlea package ?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A package is an **autonomous** piece of software.

* It can be installed independently,
* It can be in pure python or with C++ library,
* Python module are installed in the openalea namespace,
* Library and header are installed in the OpenAlea directory,
* It can be compiled on linux and on windows,
* It has documentation and tests,
* It is released under an Open Source license
* It can provide some interconnectable components.


Install your development environment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
OpenAlea packages use different programs and libraries. 
You must install and setup your `development environment <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=documentation:package:development_environment>`_ 
before being able to develop your own package.

You may work with Github, have a look on how to use Github (mettre hyperlien).. 


Implementing your package
^^^^^^^^^^^^^^^^^^^^^^^^^
When developing or porting your package, you must keep in mind that what you write must 
be easily understandable and reusable by others developers. This is a basis of the OpenAlea project.

The `coding guidelines <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=documentation:guidelines:coding_guidelines>`_ 
contains some advice to write better code that can be read by other developers.

You must also provide :

* Unit tests in order to guaranty the correctness of the module (in case of any change). 
  Read `how to write tests <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=documentation:doctests:how_to_add_unit_tests_to_your_package>`_.
* User documentation.
* Developer documentation (API). Read `how to document python API <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=documentation:doctests:how_to_document_python_api>`_ 
  and `how to document C++ API <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=documentation:doctests:how_to_document_cpp_api>`_.

Your package can be :

* A pure python module
* A python module with C++ libraries
* It is also possible to integrate Fortran code (not currently supported)

The document `how to create an OpenAlea package <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=documentation:package:how_to_create_an_openalea_package>`_ 
is a tutorial to help developers to implement their packages.

If you want to start directly with a real example, 
download the `starter package <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=packages:template:starter:starter>`_.

If your package is based on a C++ library (for efficiency reasons), 
you can read `how to integrate cpp code in python <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=documentation:package:how_to_integrate_cpp_code_in_python>`_.

Provinding OpenAlea logical components
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
`How to declare logical components <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=documentation:component:how_to_declare_logical_components>`_

Distributing your package
^^^^^^^^^^^^^^^^^^^^^^^^^
Because OpenAlea goal is to share knowledge and software development, 
an OpenAlea package must be released under an open source license.

For more information, read the `license guidelines <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=documentation:guidelines:license_guidelines>`_.

Releasing a package for OpenAlea doesn't mean that the authors loose their rights on the package. 
The authors remain the owners of the copyright and then they can decide how they 
want to distribute their packages.

The OpenAlea website can provide the visibility for your package. 
We encourage to create a page for each available package. 
Moreover, it is possible (but not mandatory) to distribute your package on the gforge platform.

The gforge repository can be used as a download server.

Read `how to distribute your package <http://openalea.gforge.inria.fr/dokuwiki/doku.php?id=documentation:package:how_to_distribute_an_openalea_package>`_.
