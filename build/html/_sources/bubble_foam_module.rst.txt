.. _section_foam_module:

Bubble and Foam Module
**************************

====================
Theory
====================

Bubble entrainment, foam transfer rate and burst rate are formulated based on empirical formulas developed in a previous study. Details will be documented in Malej et al. 2023 (in preparation). 

=================================================================
Model configuration and input
=================================================================

1) Modify Makefile with :code:`-DFOAM`

2) Specify parameters related to bubble and foam entrainments, etc.

 .. code-block:: rest
 
  PLOT_INTV_FOAM = <float number> (default: same as PLOT_INTV) 
  BurstRate = <float number> (default: 0.01)
  MinThick = <float number> (default: 0.01)
  TransferRate = <float number> (default: 0.1)
  CdFoam = <float number> (default: 0.5)

3) An example is provided in :code:`/rip\_2D\_foam/`.  The figure below shows the model result from default parameters. 


.. figure:: images/simple_cases/foam.jpg
   :width: 550px
   :align: center
   :alt: alternate text
   :figclass: align-center

==============================================================
More information
==============================================================

List of parameters for foam module setup can be found `here <https://fengyanshi.github.io/build/html/foam_para.html>`_.

============
References
============

Malej et al. (2023), in preparation.
