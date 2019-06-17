.. _OpenAlea : https://github.com/openalea

=====================================
Using Visualea : Werberpenn
=====================================

.. image:: ./images/weberpenn/intro.gif

Context
========

In OpenAlea_, different tree architectures can be generated procedurally. 
``OpenAlea.WeberPenn`` is based on the tree generating algorithm defined by Weber and Penn in 1995.

The model generate a tree structure based on a set of allometric rules.
Fundamental parameters are, for instance, the overall appearance of the tree, 
the size of the lower part of the tree without axes, the max branching order or the curvature of the axes.

Install
=========

Install Visualea and Weberpenn for this tutorial
::

    conda install -c openalea openalea.weberpenn openalea.visualea

Then, execute this
::

    visualea

Model Parameters
================

* | General shape parameters : 
  | **Scale** and **ScaleV** : Global size of the tree 
  | **BaseSize** - Size of the lower part of the tree without branches 

  Each other parameters are defined for each branch level (or **order**) with order0 = trunk

  .. image:: ./images/weberpenn/werber_param_1.jpg

* Branch **length** is specified by the user at each order and 
  is relative to the father branch length and to the overall shape of the tree.
  
  .. image:: ./images/weberpenn/werber_param_2.jpg

* **rotation** (aka rotationV) define the phyllotaxis angle at each order

  .. image:: ./images/weberpenn/werber_param_3.jpg

* | **curve** parameter defines curvature of branches 
  | **curve back** define inflexion angle

  .. image:: ./images/weberpenn/werber_param_4.jpg

* **down_angle** define the angle of insertion between a branch and its father

  .. image:: ./images/weberpenn/werber_param_5.jpg


Step 1 : Begin with Weberpenn
-----------------------------

#. Once you've launched Visualea, in the package manager, go in *demo* and double-click on ``demo_WeberPenn``.
   We will see two workflows in the workspace.

   .. image:: ./images/weberpenn/step1_1.PNG

#. On the left workflow, there are the ``global parameters``, ``trunk``, ``order 1``, ``order 2``, ``tree parameters``, 
   ``weber and penn`` and ``plot3D`` nodes.

   * ``Global parameters`` : you can change parameters of the tree globally

     .. image:: ./images/weberpenn/step1_2.PNG

   * ``trunk``, ``order 1`` and ``order 2`` : these allow to change parameters of the current order

     .. image:: ./images/weberpenn/step1_3.PNG

   * ``tree parameters`` : this node synthesizes all the parameters into a *weberpenn* object
   * ``weber and penn`` : this node creates the scene with all the generated surfaces
   * ``plot3D`` : this node displays a 3D-scene



