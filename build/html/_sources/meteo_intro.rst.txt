Meteo Module
***************

The METEO module was initially developed for simulations of meteotsnamis. It now includes subroutines for simulating the wind effects on waves, storm surges, landslide-generated tsunamis and processes related to atmospheric pressure effects. 

* Wind effect on waves

Wind effects are modeled using the wind stress forcing proposed by Chen et al. (2004). The wind stress is expressed by

.. math:: {\bf R}_w = \frac{\rho_a}{\rho} C_{dw} |{\bf U}_{10} - {\bf C}| ({\bf U}_{10} - {\bf C})

where :math:`\rho_a` and :math:`\rho` represent air density and  water density, respectively, :math:`\bf C` is wave celerity.  The wind stress is only applied on wave crests. A free parameter representing a ratio of the forced crest height to maximum surface elevation is implemented in the model. 

* Holland model

Holland model is an analytic model of wind and pressure profiles described based on Hurricanes. The pressure distribution can be expressed by 

.. math:: p = p_c + (p_n-p_c) exp(-A/r^B)

where :math:`p` is the pressure at radius :math:`r`, :math:`p_c` and :math:`p_n` are the central pressure and the ambient pressure, respectively. :math:`A` and :math:`B` are scaling paramters from the model input. The velocity distribution can be described by

.. math:: V_c = [AB(p_n-p_c)exp(-A/r^B)/\rho_a r^B]^{1/2}

Based on the formulations above, it is easy to obtain the following storm parameters

The radius of maximum winds (RMW) is

.. math:: R_w = A^{1/B}

The maximum wind speed

.. math:: V_m = C(p_n-p_c)^{1/2}

where 

.. math:: C = (B/\rho_a e)^{1/2}


* Storm surge

To calculate storm surges, wind stress is applied

.. math:: {\bf R}_w = \frac{\rho_a}{\rho} C_{dw} |{\bf U}_{10}| ({\bf U}_{10})

Note that :math:`\bf C` is not used, compared to the formula for 'Wind effect on waves'. 

* Meteotsunami

Meteotsunami is modeled using a pressure source of two-dimensional Gausian distribution:

.. math:: P = dP exp \left(-(\frac{(x^\prime - x_0)^2}{2\sigma_x^2} + \frac{(y^\prime - y_0)^2}{2\sigma_y^2}) \right)

where :math:`dP` is the pressure anomaly in mb,  :math:`(x^\prime,y^\prime)` are the coordinates rotated to the pressure moving direction (angle is :math:`\theta` as indicated in the figure). :math:`\sigma_x` and :math:`\sigma_y` are paramters representing the length of the width of the pressure source. 

.. figure:: images/gausian.jpg
    :width: 300px
    :align: center
    :height: 260px
    :alt: alternate text
    :figclass: align-center

* Landslide-generated tsunami

Landslide-generated tsunami can be calculated using the same approach as the meteotsunami. Details will be reported by Woodruff (2017). 

