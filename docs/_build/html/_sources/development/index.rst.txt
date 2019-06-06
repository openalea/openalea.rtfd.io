.. _developers:

===========
Development
===========

.. contents::

Contributing
============

Introduction
------------

This project is an open-source one, it is intended that everyone is welcome to contribute.

This project is hosted on different levels on GitHub.

Here is the official and stable repository `https://github.com/openalea <https://github.com/openalea>`_
and here is the working repository used for testing `https://github.com/openalea-incubator <https://github.com/openalea-incubator>`_.

Later on, it will be explained how to use these two repository.

There are many ways to contribute to OpenAlea. The most common ways of contributing are coding or documenting different parts of 
the project. One may improve documentation which is as much important as improving the code itself. 
One could also create their own package, see `How to contribute`_.

Another way to contribute to the project is to report bugs ans issues you are facing.

How to contribute
-----------------

The main way to contribute is to fork the package repository you are interested in on GitHub 
(be careful, some are on `OpenAlea GitHub <https://github.com/openalea>`_, 
some are on `OpenAlea-Incubator GitHub <https://github.com/openalea-incubator>`_), then submit "a pull request".

#. `Create an account <https://github.com/join>`_ on GitHub if you do not already have one.

#. Fork the package repository of your choice (for instance, `mtg repository <https://github.com/openalea/mtg>`_) and click on 
   the 'Fork' button near the top of the page. It generates a copy of the repository under your
   account on the GitHub user account. For more details on how to fork a
   repository see `this guide <https://help.github.com/articles/fork-a-repo/>`_.

#. Clone your fork of the package repo from your GitHub account to your
   local disk

   HTTPS clone::
	
       git clone https://github.com/YourLogin/PackageName.git

   SSH clone::

       git clone git@github.com:YourLogin/PackageName.git

   then change directory::

       cd PackageName

#. Create a branch to hold your development changes::

       git checkout -b YourNewFeature

   and start making changes. Always use a ``feature`` branch. It's good practice to
   never work on the ``master`` branch!

   .. note::

     In the above setup, your ``origin`` remote repository points to
     ``YourLogin/.git``. If you wish to fetch/merge from the main
     repository instead of your forked one, you will need to add another remote
     to use instead of ``origin``. It's good practice to choose the name ``upstream`` for it, and the
     command will be::

         git remote add upstream https://github.com/openalea(-incubator)/PackageName.git

     And in order to fetch the new remote and base your work on the latest changes
     of it you can::

         git fetch upstream
         git checkout -b YourNewFeature upstream/master

#. Develop the feature on your feature branch on your computer, using Git to do the
   version control. When you're done editing, add changed files using ``git add``
   and then ``git commit`` files::

       git add ModifiedFiles
       git commit -m "Description of what you've done"

   to record your changes in Git, then push the changes to your GitHub account with::

       git push -u origin YourNewFeature

#. Once you've finished, you can create a "pull request" on the corresponding GitHub. 
   Follow `these
   <https://help.github.com/articles/creating-a-pull-request-from-a-fork>`_
   instructions to create a pull request from your fork.

How to make a proper bug report
-------------------------------

Documentation
-------------
