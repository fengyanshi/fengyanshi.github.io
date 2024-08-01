.. funwave documentation master file, created by
   sphinx-quickstart on Fri Apr 14 11:58:54 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. role:: raw-html(raw)
   :format: html

========================
FUNWAVE-TVD
========================
`Switch to USACE Version <index.html>`_

FUNWAVE--TVD is the Total Variation Diminishing (TVD) version of the fully nonlinear Boussinesq wave model (FUNWAVE) developed by `Shi et al. (2012) <http://www.sciencedirect.com/science/article/pii/S1463500311002010>`_. The FUNWAVE model was initially developed by `Kirby et al. (1998) <http://resolver.tudelft.nl/uuid:d79bba08-8d35-47e2-b901-881c86985ce4>`_ based on `Wei et al. (1995) <https://doi.org/10.1017/S0022112095002813>`_. The development of the present version was motivated by recent needs for modeling of surfzone--scale optical properties in a Boussinesq model framework, and  modeling of Tsunami waves in both a global/coastal scale for prediction of coastal inundation and a basin scale for wave propagation.

This version  features  several theoretical and numerical improvements, including:

.. image:: images/coverimage.jpg
   :width: 500px
   :height: 200px
   :align: right

1. A more complete set of fully nonlinear Boussinesq equations; 
2. Monotonic Upwind Scheme for Conservation Laws (MUSCL)--TVD solver with adaptive Runge--Kutta time stepping; 
3. Shock--capturing wave breaking scheme; 
4. Wetting--drying moving boundary condition with incorporation of Harten-Lax-van Leer (HLL) construction method into the scheme; 
5. Lagrangian tracking;
6. Option for parallel computation. 

==========
Subscribe
==========

Stay connected to the global FUNWAVE community by subscribing to the mailing group. Submit general or specific questions to new and experienced users alike to solve problems and enhance solutions.

.. raw:: html
   :file: google_group.html
   
Stay up-to-date on the latest video tutorials and examples on YouTube by subscribing to `FUNWAVE Tutorials <https://www.youtube.com/channel/UCIWsla9RSOGaxoVFExGuK_w>`_ and `Fengyan Shi <https://www.youtube.com/channel/UCWmlY0Lpr8e0qnLGvlYLW1g>`_.

============
Wiki Content
============
.. toctree::
   :maxdepth: 2

   what_is_funwave
   where_start
   basics
   flowchart
   setup
   tutorials
   definition
   coupling_nesting
   examples
   gallery
   news
   references
   authors

Indices and tables
******************

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
