.. _section-sedi-module:

Sediment Transport Module
****************************

Module framework:

.. figure:: images/modules/sediment_chart_1.png
    :width: 400px
    :align: center
    :height: 275px
    :alt: alternate text
    :figclass: align-center

Fundamental equations
=====================

**Depth-averaged sediment concentration equation**

.. math:: (\bar{c}H)_{t} + \nabla_{h} \cdot (\bar{c}H(\textbf{u}_{\alpha} + \bar{\textbf{u}}_2)) = \nabla_{h} \cdot (kH(\nabla_{h}\bar{c})) + P - D 

Pick up function (`van Rijn 1984 <https://doi.org/10.1061/(ASCE)0733-9429(1984)110:10(1494)>`_):

.. math:: P = 0.015\frac{d_{50}}{a} \left( \frac{|\tau_b|-\tau_{cr}}{\tau_{cr}} \right)^{1.5} d_{*}^{-0.3} \omega_{f}, \ \ \ \ \ |\tau_b| > \tau_{cr}

Deposition rate (`Cao 1999 <https://doi.org/10.1061/(ASCE)0733-9429(1999)125:12(1270)>`_):

.. math:: D = \gamma \bar{c} \omega_{f} (1-\gamma\bar{c})^{m_o}

**Bedload formula**

`Meyer-Peter and Muller (1948) <http://resolver.tudelft.nl/uuid:4fda9b61-be28-4703-ab06-43cdc2a21bd7>`_:

.. math:: q_b = \frac{8 [(\tau_b - \tau_{cr}^b) / \rho_{\omega}]^{3/2}}{g(s-1)}

**Bed evolution equation**

.. math:: \frac{dZ_{b}}{dt} = \frac{1}{1-n} (D-P-\nabla \cdot \overrightarrow{q}_b )

.. image:: images/modules/sediment.png
   :width: 500px
   :height: 250px
   :align: center

DETAILS
=======

.. toctree::
   :maxdepth: 2

   sed_equation
   sed_equation_cohesive
   bedload
   bed_equation
   sed_hydro_correction
   slope_limiting
   non_erodible
   sed_numerical
   sed_propeller

APPLICATIONS
============

* `Ocean City Tsunami Inundation Map <ocean_city_dune.html>`_

* `2011 Tohoku-Oki tsunami impact in Crescent City harbor <tohoku_crescent.html>`_

   `more results of Crescent City Case <https://drive.google.com/open?id=1qwTSWZZaQjQWZAj6mt4JzBqaPrYHyJGH>`_

**References**

Cao, Z., (1999). "Equilibrium Near-Bed Concentration of Suspended Sediment". J. of Hydraulic Eng., 125 (12). DOI: 10.1061/(ASCE)0733-9429(1999)125:12(1270).

Meyer-Peter, E., and Muller, R., (1948). "Formulas for Bed-Load transport". Hydraulic Eng. Reports: IAHSR 2nd meeting, Stockholm, Appendix 2. IAHSR.

van Rijn, L.C., (1984). "Sediment Pick-Up Functions". J. of Hydraulic Eng., 110 (10). DOI: 10.1061/(ASCE)0733-9429(1984)110:10(1494).


`Back to FUNWAVE-TVD Page <https://fengyanshi.github.io/build/html/index.html>`_


