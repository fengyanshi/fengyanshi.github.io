Sediment Transport Equation
******************************

The sediment transport module is based on the quasi-steady flow-based approach. The morphological module calculates the bed evolution based on sediment continuity equation. 

Sediment motion is governed by the depth-averaged sediment concentration equation as follows,

.. math:: (\bar{c} H)_t + \nabla_h \cdot (\bar{c} H ({\bf u}_\alpha + \bar{{\bf u} }_2)) =\nabla_h \cdot (k H (\nabla_h \bar{c})) + P - D \label{ad}

where :math:`\bar{c}` is the non-dimensional depth-averaged sediment concentration normalized by sediment density. :math:`H(\bf{u}_\alpha + \bar{\bf{u}}_2) =M` represents the flow rate per unit width defined in Shi et al. (2012), in which :math:`H=h+\eta` is the total water depth. :math:`k` is the horizontal sediment diffusion coefficient calculated by the formula given by Elder (1959),

.. math:: k = 5.93 u_{*c} H

where :math:`u_{*c}` is the shear velocity and can be calculated by (van Rijn, 1984)

.. math:: u_{*c} = \frac{\kappa}{-1 + \log (30 H / k_s)} U_c

in which :math:`U_c` is the depth-averaged total velocity, :math:`k_s = 2.5 d_{50}` is Nikuradse roughness coefficient, and :math:`d_{50}` is the median grain diameter.  
 
In the advection-diffusion equation, :math:`P` and :math:`D` represent the erosion rate and deposition rate, respectively. The erosion rate can be calculated using van Rijn's (1984) pickup function,

.. math:: P = 0.015 \frac{d_{50}}{a} \left ( \frac{|\tau_b| - \tau_{cr}}{\tau_{cr}}\right ) d^{-0.3}_{*} w_f \label{p}

where :math:`a` is a reference elevation and is a function of total depth (:math:`a = 0.01 H`), :math:`\tau_b` is the bed shear stress, and :math:`\tau_{cr}` is the critical shear stress. :math:`P` has the dimension of velocity (m/s) considering the convection-diffusion equation for non-dimensional sediment concentration. :math:`d_{*}` is dimensionless grain size defined as

.. math:: d_{*} = d_{50} \left( \frac{(s-1)g}{\nu^2} \right)^{1/3}

where :math:`s` is the specified gravity of the sediment, and :math:`\nu` is the kinematic viscosity coefficient. The critical bed shear stress :math:`\tau_{cr}` used in (\ref{p}) is defined as,

.. math:: \tau_{cr} = \rho_w (s-1)gd_{50} \theta_{cr}

where :math:`\theta_{cr}` is the critical Shields parameter, approximately equal to 0.05. Based on the roughness estimate, the shear stress is expressed as

.. math:: |\tau_b| = \frac{\rho_w k^2}{1+\ln (k_s/30 h)} U_c

The deposition rate :math:`D` can be calculated using the formula of Cao (1999),

.. math:: D = \gamma c w_f (1-\gamma \bar{c})^{m_o}

where :math:`\gamma = \min [2,(1-n/\bar{c})]`, :math:`n` is the sediment porosity, and :math:`m_0` is a constant number given as 2.0. 
