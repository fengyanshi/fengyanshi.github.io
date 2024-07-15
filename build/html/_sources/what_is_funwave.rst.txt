

**What is FUNWAVE-TVD?**
==========================
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

The most recent developments include ship-wake generation (`Shi et al., 2018 <https://www.sciencedirect.com/science/article/pii/S0378383917304246>`_), meteo-tsunami generation (`Woodruff et al., 2018 <https://icce-ojs-tamu.tdl.org/icce/index.php/icce/article/view/8470>`_), and sediment transport and morphological changes (`Tehranirad et al., 2016 <https://coastal.udel.edu/research-2/cacr-reports/>`_, `Malej et al., 2019 <https://apps.dtic.mil/dtic/tr/fulltext/u2/1074624.pdf>`_).

