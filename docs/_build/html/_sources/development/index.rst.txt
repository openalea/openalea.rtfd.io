.. _developers:
.. _OpenAlea: https://github.com/openalea
.. _OpenAlea-Incubator: https://github.com/openalea-incubator
.. _GitHub: https://github.com
.. _Fork: https://help.github.com/en/articles/fork-a-repo
.. _Clone: https://help.github.com/en/articles/cloning-a-repository

===========
Development
===========

.. contents::

Contributing
============

Introduction
------------

OpenAlea_ is open-source. Everyone is welcome to contribute.

.. note::

  All the packages are separated on two Github_ pages

  * the official and stable packages on OpenAlea_
  * the unofficial, WIP and *to be reviewed* packages on OpenAlea-Incubator_

There are many ways to contribute to OpenAlea_. The most common ways of contributing are coding or documenting different parts of 
the project. One may improve documentation which is as much important as improving the code itself. 
One could also create their own package, see `How to contribute`_.

Another way to contribute to the project is to report bugs ans issues you are facing.

How to contribute
-----------------

The main way to contribute is to fork the package repository you are interested in on GitHub_ 

.. note:: 

  Remember, the packages are found on different GitHub_ pages. The following steps describe a tutorial for an OpenAlea_ package.
  Make the good changes if you want to use OpenAlea-Incubator packages.

#. `Create an account <https://github.com/join>`_ on GitHub if you do not already have one. 
   You will choose your GitHub_ login <your_login>.

#. Fork_ the package repository of your choice (for instance, `MTG repository <https://github.com/openalea/mtg>`_) and click on 
   the 'Fork_' button near the top of the page. It generates a copy of the repository under your
   account on the GitHub_ user account. For more details on how to fork a
   repository see `this guide <https://help.github.com/articles/fork-a-repo/>`_.

#. Clone_ your fork of the package repo from your GitHub_ account to your
   local disk
   ::	
       
       git clone https://github.com/<your_login>/<package_name>.git
       cd <package_name>

#. Create a branch <branch_name> to hold your development changes
   ::

       git checkout -b <branch_name>

   and start making changes. Always use a ``feature`` branch. It's good practice to
   never work on the ``master`` branch!

   .. note::

     In the above setup, your ``origin`` remote repository points to
     ``<your_login>/.git``. If you wish to fetch/merge from the main
     repository instead of your forked one, you will need to add another remote
     to use instead of ``origin``. It's good practice to choose the name ``upstream`` for it, and the
     command will be::

         git remote add upstream https://github.com/openalea/<package_name>.git

     .. note::

       If the package you chose come from OpenAlea-Incubator, the command will be::

           git remote add upstream https://github.com/openalea_incubator/<package_name>.git

     And in order to fetch the new remote and base your work on the latest changes
     of it you can::

         git fetch upstream
         git checkout -b <your_name> upstream/master

#. Develop the feature on your feature branch on your computer, using Git to do the
   version control. When you're done editing, add changed files using ``git add``
   and then ``git commit`` files::

       git add <modified_files>
       git commit -m "description of what you've done"

   to record your changes in Git, then push the changes to your GitHub_ account with::

       git push -u origin <branch_name>

#. Once you've finished, you can create a **pull request** on the corresponding GitHub_. 
   Follow `these
   <https://help.github.com/articles/creating-a-pull-request-from-a-fork>`_
   instructions to create a pull request from your fork.

How to make a proper bug report
-------------------------------

Documentation
-------------
