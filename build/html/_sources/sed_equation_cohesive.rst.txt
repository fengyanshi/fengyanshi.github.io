.. _section_sed_equation_cohesive:

Suspended Sediment Transport Equation (Cohesive)
***************************************************

The transport equation for cohesive sediment uses the same 2D form of advection and diffusion equation as that used for non-cohesive sediment:  

.. math:: (\bar{c} H)_t + \nabla_h \cdot (\bar{c} H ({\bf u}_\alpha + \bar{{\bf u} }_2)) =\nabla_h \cdot (k H (\nabla_h \bar{c})) + P - D \label{ad}

where :math:`\bar{c}` is the non-dimensional depth-averaged sediment concentration normalized by sediment density. :math:`H(\bf{u}_\alpha + \bar{\bf{u}}_2) =M` represents the flow rate per unit width defined in `Shi et al. (2012) <http://www.sciencedirect.com/science/article/pii/S1463500311002010>`_, in which :math:`H=h+\eta` is the total water depth. The roller-induced extra undertow can be taken into account as an option (see :ref:`section-wavebreaking`, and :ref:`section-physics`). :math:`k` is the horizontal sediment diffusion coefficient used for cohesive sediment and is usually defined by users (such as in the `DHI model <https://www.mikepoweredbydhi.com/products/mike-21/sediments>`_). Some researchers showed that the diffusion coefficient is a function of current flux, such as in `Kimiaghalam et al. (2019) <http://www.nrcresearchpress.com/doi/abs/10.1139/cjce-2015-0361#.XXo-2ZNKjjA>`_ who connected the diffusion coefficient to river discharges. 
 
In the advection-diffusion equation, :math:`P` and :math:`D` represent, respectively, the erosion rate and deposition rate for cohesive sediment. There are two sets of formulas to calculate the erosion rate. For hard bed, `Partheniades' (1965) formula <https://cedb.asce.org/CEDBsearch/record.jsp?dockey=0013640>`_ is used:

.. math:: P = E \left(\frac{\tau_b}{\tau_{cr}} -1 \right)

For soft bed, `Parchure and Mehta's (1985) formula  <https://ascelibrary.org/doi/10.1061/%28ASCE%290733-9429%281985%29111%3A10%281308%29>`_ is applied:

.. math:: P = E e^{\alpha \sqrt{\tau_b-\tau_{cr}}}

where :math:`E` is the erodibility specified by users, :math:`\tau_b` is the bed shear stress, and :math:`\tau_{cr}` is the critical shear stress for erosion.  The bed shear stress can be calculated using Soulsby et al. (1993):


.. math:: \tau_b = \rho_w \left(\frac{ 0.4}{1+\ln (k_s/30 h)} \right)^2 U_c^2

which is the same as for the non-cohesive sediment, and the critical bed shear stress is usually specified by users. For soft bed, :math:`\alpha` is a so-called alpha-coefficient specified by users. 

The erosion rate, :math:`P`, has the dimension of velocity (m/s) considering the convection-diffusion equation for non-dimensional sediment concentration. 

The deposition rate :math:`D` can be calculated using the formula of `Krone (1962) <https://www.worldcat.org/title/flume-studies-of-the-transport-of-sediment-in-estuarial-shoaling-processes-final-report/oclc/8967084>`_:

.. math:: D = w_s c_b p_d  
   :label: depo

where :math:`w_s` is the settling velocity which can be evaluated using a number of formulas from different sources and usually based on laboratory experiments. It should be related to processes of flocs, aggregate dimensions, drag, local concentration, salinity and other environmental factors. Users can define their own formulas by modifying the sediment module. Here, we provide a general formulation that can describe the evolution in conditions of flocculation (In `Kombiadou and Krestenitis, 2014 <http://dx.doi.org/10.5772/51061>`_):

.. math:: w_s = \frac{a \bar{c}^n}{(\bar{c}^2 + b^2)^m}

The coefficients have a large range, differing in various estuarine and riverine areas. :math:`a=0.01-0.23, b=1.3-25.0, n=0.4-2.8` and :math:`m=1.0-2.8`. The default values in the model are
:math:`a=0.1;
b=2.0;
n=0.5;
m=1.5.`
For :math:`\bar{c}=0.1 g/l`, for example, :math:`w_s = 3.9E^{-3} m/s`. 


In :eq:`depo`, :math:`c_b` is the near-bed concentration calculated by

.. math:: c_b = \beta \bar{c}

in which :math:`\beta` is the parameter. By default, we use :math:`\beta = 1`. It can also be specified by

.. math:: \beta = 1+\frac{P_e}{1.25+4.75 p_d^{2.5}}

where :math:`P_e` is the Peclet number:

.. math:: P_e = \frac{6 w_s}{\kappa u_{*c}}

in which :math:`\kappa` is von Karman constant and :math:`u_{*c}` is the friction velocity which can be calculated by `van Rijn (1984) <10.1061/(ASCE)0733-9429(1984)110:10(1494)>`_:

.. math:: u_{*c} = \frac{\kappa}{-1 + \log (30 H / k_s)} U_c

:math:`P_d` is the probability of deposition defined by

.. math:: P_d = 1- \left( \frac{\tau_b}{\tau_{cd}} \right)

where :math:`\tau_{cd}` is the critical shear stress for deposition defined by users. 

**Summary of Input Parameters**

1) :math:`k`: diffusion coefficient, k_coh (default 10E-6). Different from the non-cohesive sediment transport, this parameter needs to be specified by users. 

2) :math:`\tau_{cr}`: critical shear stress for erosion, Tau_cr_coh (default 0.001)

3) :math:`\tau_{cd}`: critical shear stress for deposition, Tau_crd_coh (default 0.001)

4) :math:`a,b,m` and :math:`n`: Empirical parameters used to calculate settling velocity, default values are a_coh = 0.1, b_coh=2.0, n_coh=0.5, and m_coh=1.5

5) :math:`E`: erodibility parameter, default E_coh=0.0001

6) :math:`\alpha`: alpha-coefficient used to calculate the erosion rate for soft bed, default alpha_coh = 1.0 

An example of model setup can be found in /simple_cases/single_vessel_cohesive/. See :ref:`section-vessel-sediment-cohesive` for documentation. 

**References**

Kimiaghalam, N., Goharrokhi,M., Clark, S. P., 2016, Estimating cohesive sediment erosion and deposition rates in wide rivers, Canadian Journal of Civil Engineering, 43(2): 164-172 `doi.org/10.1139/cjce-2015-0361 <http://www.nrcresearchpress.com/doi/abs/10.1139/cjce-2015-0361#.XXo-2ZNKjjA>`_

Krone, R. B., 1962, Flume Studies of the Transport of Sediment in Estuarine Shoaling Processes. Final Report to San Francisco District U. S. Army Corps of Engineers, Washington D.C. `website for Krone 1962 <https://www.worldcat.org/title/flume-studies-of-the-transport-of-sediment-in-estuarial-shoaling-processes-final-report/oclc/8967084>`_

Parchure, T. M. and A. J. Mehta, 1985, Erosion of soft cohesive sediment deposits, Journal of Hydraulic Engineering – ASCE 111 no. 10: 1308–1326 `doi/10.1061  <https://ascelibrary.org/doi/10.1061/%28ASCE%290733-9429%281985%29111%3A10%281308%29>`_

Partheniades, E. 1965, Erosion and deposition of cohesive soils, Journal of the hydraulics division. Proceedings of the ASCE 91 no. HY1: 105–139 `website for Partheniades 1965 <https://cedb.asce.org/CEDBsearch/record.jsp?dockey=0013640>`_

Parchure, T. M. and A. J. Mehta, 1985, Erosion of soft cohesive sediment deposits, Journal of Hydraulic Engineering – ASCE 111 no. 10: 1308–1326 `doi:10.1061 <https://ascelibrary.org/doi/10.1061/%28ASCE%290733-9429%281985%29111%3A10%281308%29>`_

Shi, F., J.T. Kirby, J.C. Harris, J.D. Geiman, and S.T. Grilli, 2012, A high-order adaptive time-stepping TVD solver for Boussinesq modeling of breaking waves and coastal inundation. Ocean Modelling, 43-44: 36-51. `DOI: 10.1016/j.ocemod.2011.12.004 <http://www.sciencedirect.com/science/article/pii/S1463500311002010>`_

Soulsby R. L., Hamm L., Klopman, G., Myrhaug, D., Simons R.R., Thomas, G. P., 1993, Wave-current interaction within and outside the bottom boundary layer, Coastal Engineering, Volume 21, Issues 1–3, December 1993, Pages 41-69, `doi:10.1016/0378-3839(93)90045-A <https://doi.org/10.1016/0378-3839(93)90045-A>`_

van Rijn, L.C., 1984, Sediment Pick‐Up Functions, Journal of Hydraulic Engineering
Vol. 110, Issue 10 (October 1984) `doi:10.1061/(ASCE)0733-9429(1984)110:10(1494) <https://doi.org/10.1061/(ASCE)0733-9429(1984)110:10(1494)>`_
