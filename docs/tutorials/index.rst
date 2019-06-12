==========================
Visualea Beginner Tutorial
==========================

Here is a tutorial in which you will see how to implement a simple modeling problem in *Visualea*
Once you installed and activated the OpenAlea environment (see `Installation <https://openaleadocs.readthedocs.io/en/latest/install.html>`_), execute this 
::

    $visualea

The Goal
========

We measured some tree data and saved these in a tabbed editor (like Excel). The data have been exported in a CSV file. We want to have a simple 3D representation  of the measured tree.

Here is the data :

.. csv-table::
   :header: "X", "Y", "crown_up", "crown_bot", "trunk_diameter"
   :widths: 15, 15, 20, 20, 20

   0, 0, 10, 20, 2
   10, 12, 12, 18, 3
   20, 22, 8, 23, 3.4
   0, 18, 14, 22, 2.5

You may want to download the `CSV file <http://openalea.gforge.inria.fr/dokuwiki/lib/exe/fetch.php?media=documentation:tutorials:stand.csv>`_.

Step 1 : Create Your Own Package
================================

First of all, we need to create a package where to put your work (dataflow, node definition, data, …). A package is in fact a simple directory containing python files.

Create a package
----------------

#. Select **Package Manager** -> **Add* -> **Package**
#. Fill the form : 
   * **Name** : standbuilder
   * **Description** : build stand representation from measured data
   * **Version** : 0.1
   * **License** : Cecill-C
   * **Authors** : All collaborators and package writer
   * **Institutes** : …
   * **URL** : …
   * **Path** : /home/myhome/openalea_pkg (could be anywhere you want)
#. Click "OK"

Yuur new package should appear in the package manager.

.. tip::
   The path corresponds to the directory where the python file will be written. 
   Choose it carefully in order to be able to find it later.


Step 2 : Read CSV Data
======================

Create a dataflow to read and view a file
-----------------------------------------

.. tip::
   Leaving the cursor on any item in the Package Manager, or on nodes or ports in 
   the dataflow view brings up a tooltip. Clicking on them also shows some documentation 
   in the “Help” tab (bottom-left-hand corner).

#. In the Package Manager tab (left column), open the ``openalea.file`` folder. You should 
   see a list of nodes.
   
   .. note::
      You can search for a particuliar node in the Search tab.

#. In the Package Manager tab, drag the ``read`` node from the *openalea.file* package to the 
   workshop. It should now appear on the canvas.
#. In the workspace, right click on the ``read`` node and choose "Open Widget". 
   Then browse for the "stand.csv" file (no need to validate anything, 
   changes are automatically taken into account so you can simply close the window).
#. Drag the ``text`` node from the *openalea.data structure.string* folder onto the workspace.
#. Connect the output of the ``read`` node to the input of the ``text`` node.
