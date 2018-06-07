Bedload Sediment Transport
**************************************
Bedload sediment transport can be calculated using several bedload sediment transport formulas developed for steady flows. As stated in Soulsby (1997), those formulas can be used on an instantaneous basis in tidal flows, and under waves or combined waves and currents, because the response time of a sand grain in bedload motion is very short compared to a tidal period or a wave period. In test examples provided in the wiki, we used Meyer-Peter and Muller's (1948) bedload transport formula to estimate the bedload sediment transport rate and its effect on bed evolution.  The unit-width volume transport rate can be expressed as

.. math::   q_b = 8 [g(s-1)d^3]^{1/2}(\theta-\theta^b_{cr})^{3/2}

where :math:`\theta` is the Shields parameter and :math:`\theta^b_{cr}` is the critical Shields parameter for bedload motion. In Meyer-Peter and Muller (1984),  :math:`\theta^b_{cr} = 0.047`.
 
After reorganizing the formula using the bed shear stress form, the formula can be rewritten as

.. math::  q_b = \frac{8 [(\tau_b-\tau^b_{cr})/\rho_w]^{3/2}}{g(s-1)}

where :math:`\tau^b_{cr}` is the critical shear stress for bedload motion which can be calculated using :math:`\theta^b_{cr}`.

