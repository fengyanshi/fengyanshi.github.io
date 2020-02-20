.. _section_sed_equation:

Suspended Sediment Transport Equation (Non-cohesive)
******************************************************

The sediment transport module calculates sediment transport induced by both suspended load and bedload. The morphological module calculates the bed evolution based on the sediment continuity equation.

Suspended sediment motion is governed by the depth-averaged sediment concentration equation as follows:

.. math:: (\bar{c} H)_t + \nabla_h \cdot (\bar{c} H ({\bf u}_\alpha + \bar{{\bf u} }_2)) =\nabla_h \cdot (k H (\nabla_h \bar{c})) + P - D \label{ad}

where :math:`\bar{c}` is the non-dimensional depth-averaged sediment concentration normalized by sediment density. :math:`H(\bf{u}_\alpha + \bar{\bf{u}}_2) =M` represents the flow rate per unit width defined in `Shi et al. (2012) <http://www.sciencedirect.com/science/article/pii/S1463500311002010>`_, in which :math:`H=h+\eta` is the total water depth. The roller-induced extra undertow can be taken into account as an option (see :ref:`section-wavebreaking`, and :ref:`section-physics`). :math:`k` is the horizontal sediment diffusion coefficient calculated by the formula given by `Elder (1959) <https://www.cambridge.org/core/services/aop-cambridge-core/content/view/310194D66B91765946845BB274E59F7F/S0022112059000374a.pdf/dispersion_of_marked_fluid_in_turbulent_shear_flow.pdf>`_:

.. math:: k = 5.93 u_{*c} H

where :math:`u_{*c}` is the shear velocity and can be calculated by `van Rijn (1984) <10.1061/(ASCE)0733-9429(1984)110:10(1494)>`_:

.. math:: u_{*c} = \frac{\kappa}{-1 + \log (30 H / k_s)} U_c

in which :math:`U_c` is the depth-averaged total velocity (m/s), :math:`k_s = 2.5 d_{50}` is Nikuradse roughness coefficient, and :math:`d_{50}` is the median grain diameter (mm).  
 
In the advection-diffusion equation, :math:`P` and :math:`D` represent the erosion rate and deposition rate, respectively. The erosion rate can be calculated using van Rijn's (1984) pickup function:

.. math:: P = 0.015 \frac{d_{50}}{a} \left ( \frac{|\tau_b| - \tau_{cr}}{\tau_{cr}}\right ) d^{-0.3}_{*} w_f 
    :label: p

where :math:`a` is a reference elevation and is a function of total depth (:math:`a = 0.01 H`), :math:`\tau_b` is the bed shear stress, and :math:`\tau_{cr}` is the critical shear stress. :math:`P` has the dimension of velocity (m/s) considering the convection-diffusion equation for non-dimensional sediment concentration. :math:`d_{*}` is dimensionless grain size defined as:

.. math:: d_{*} = d_{50} \left( \frac{(s-1)g}{\nu^2} \right)^{1/3}

where :math:`s` is the specified gravity of the sediment, and :math:`\nu` is the kinematic viscosity coefficient. The critical bed shear stress :math:`\tau_{cr}` used in :eq:`p` is defined as:

.. math:: \tau_{cr} = \rho_w (s-1)gd_{50} \theta_{cr}

where :math:`\theta_{cr}` is the critical Shields parameter, approximately equal to 0.05. Based on the roughness estimate, the shear stress is expressed as:

.. math:: \tau_b = \rho_w \left(\frac{ 0.4}{1+\ln (k_s/30 h)} \right)^2 U_c^2

The deposition rate :math:`D` can be calculated using the formula of `Cao (1999) <https://ascelibrary.org/doi/pdf/10.1061/%28ASCE%290733-9429%281999%29125%3A12%281270%29>`_:

.. math:: D = \gamma c w_f (1-\gamma \bar{c})^{m_o}

where :math:`\gamma = \min [2,(1-n/\bar{c})]`, :math:`n` is the sediment porosity, and :math:`m_0` is a constant number given as 2.0. 

**References**

Cao, Z. (1999) "Equilibrium near-bed concentration of suspended sediment". *J. of Hydraulic Eng.*, 125(12): 1270-1278. DOI: 10.1061/(ASCE)0733-9429(1999)125:12(1270).

Elder, J.W. (1959). "The dispersion of marked fluid in turbulent shear flow". *J. of Fluid Mech.*, 5(4): 544-560. DOI: 10.1017/S0022112059000374.

Shi, F., J.T. Kirby, J.C. Harris, J.D. Geiman, and S.T. Grilli, (2012). "A high-order adaptive time-stepping TVD solver for Boussinesq modeling of breaking waves and coastal inundation". *Ocean Modelling*, 43-44: 36-51. DOI: 10.1016/j.ocemod.2011.12.004.

