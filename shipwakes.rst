.. _section-shipwake-mod:

Ship-wake Module 
****************

We have implemented various types of source functions for ship-wave generation. 
 

**1) PRESSURE SOURCE TYPE I**


Following `Ertekin et al. (1986) <https://doi.org/10.1017/S0022112086000630>`_, `Wu (1987) <https://doi.org/10.1017/S0022112087002817>`_, and `Torsvik et al. (2008) <https://doi.org/10.1061/(ASCE)0733-950X(2009)135:3(120)>`_, the pressure disturbance with a center point at :math:`(x^*, y^*)` is given by:

.. math:: p_a(\tilde{x},\tilde{y},t) = P f(\tilde{x},t) q(\tilde{y},t),

where:

.. math:: f(\tilde{x},t) = \left \{ \begin{array}{rl} \cos^2\left [\frac{\pi(\tilde{x}-x^*(t)-\frac{1}{2}\alpha_1 L)}{(1-\alpha_1) L} \right ], & \frac{1}{2}\alpha_1 L < \tilde{x} - x^*(t) \le \frac{1}{2}L \\ \cos^2\left [\frac{\pi(x^*(t)-\tilde{x}-\frac{1}{2}\alpha_2 L)}{(1-\alpha_2) L} \right ], & -\frac{1}{2}L \le \tilde{x}-x^*(t) \lt -\frac{1}{2}\alpha_2 L \\1, &  - \frac{1}{2}\alpha_2 L \le \tilde{x} - x^*(t) \le \frac{1}{2}\alpha_1 L \end{array} \right.

.. math:: q(\tilde{y},t) = \left \{ \begin{array}{rl} \cos^2 \left [\frac{\pi(|\tilde{y}-y^*(t)|-\frac{1}{2}\beta W)}{(1-\beta) W} \right ], & \frac{1}{2}\beta W < |\tilde{y} - y^*(t)| \le \frac{1}{2}W \\ 1, &  |\tilde{y} - y^*(t)| \le \frac{1}{2}\beta W \end{array} \right.

In the rectangle, :math:`- L/2 \le \tilde{x} - x^*(t) \le L/2`  and  :math:`- W/2 \le \tilde{y} - y^*(t) \le R/2`, and zero outside this region; :math:`L` and :math:`W` represent the length and width of the pressure source, respectively. :math:`\alpha_1`, :math:`\alpha_2` and :math:`\beta` are parameters representing the shape of the draft region, and :math:`0\le(\alpha_1, \alpha_2, \beta)<1`. They can be evaluated using the block coefficient of a watercraft as described below. (:math:`\tilde{x}, \tilde{y}`) is the coordinate system for the pressure disturbance which may be rotated by an angle relative to the Boussinesq coordinate system (:math:`x,y`). :math:`P` is a parameter controlling the surface displacement. In fact, :math:`p_a` is the static depression around the vessel.  

In contrast to the formulation of the pressure distribution in the previous study (`Torsvik et al., 2008 <https://doi.org/10.1061/(ASCE)0733-950X(2009)135:3(120)>`_),  :math:`P` has a unit of meters and can be interpreted as the inverse barometer effect corresponding to the static surface depression for a stationary vessel. 

The values of :math:`\alpha_1`, :math:`\alpha_2`, and :math:`\beta` are shape parameters and can be obtained by adjusting :math:`\alpha_1`, :math:`\alpha_1` and :math:`\beta` to get the displaced volume (static submerged volume of the vessel):

.. math:: V_{\mbox{sub}} = \iint p_a d\tilde{x} d\tilde{y}

which should match a given block coefficient :math:`C_B` defined by:

.. math:: C_B = \frac{V_{\mbox{sub}} }{L \cdot W \cdot D}

in which :math:`D` represents draft of a vessel. 

**2) PRESSURE SOURCE TYPE II**

Type II of the pressure-type source is formulated following `Bayrakter and Beji (2013) <https://doi.org/10.1016/j.oceaneng.2012.12.025>`_. `David et al. (2017) <https://doi.org/10.1016/j.coastaleng.2017.07.001>`_ used this formulation in their tests. The pressure source can be written as:

.. math:: p_a(\tilde{x},\tilde{y},t) = P \left[1-a(\tilde{x}/L)^4  \right] \left[1-b(\tilde{y}/W)^2  \right] e^{-c(\tilde{y}/W)^2}

where :math:`a`, :math:`b` and :math:`c` are form parameters. For a slender body, :math:`a=16.0`, :math:`b=2.0` and :math:`c=16.0`.  

**3) SLENDER SOURCE TYPE I**

For the slender-type source, the additional volume flux induced by ship motion is applied in the mass conservation equation:

.. math:: dQ = F * \sin (2\pi (\tilde{x}-x^*(t)/L) * \cos (2\pi (\tilde{y}-y^*(t))/W)

where :math:`dQ` represents the flux gradient. :math:`F` is a parameter which can be determined by the block ratio. The formula is calculated in the rectangle :math:`- L/2 \le \tilde{x} - x^*(t) \le L/2`  and  :math:`- W/2 \le \tilde{y} - y^*(t) \le R/2`, and zero outside this region.

**4) SLENDER SOURCE TYPE II**

The Type II of the slender source is similar to the Type I but with two additional parameters representing sizes of bow and stern:
 
.. math:: dQ = \left \{ \begin{array}{rl} F * \sin (2\pi ((\tilde{x}-x^*(t)-\frac{1}{2}\alpha_1 L)/(1-\alpha_1)L) * \cos (\pi \tilde{y}/W), &  \frac{1}{2}\alpha_1 L < \tilde{x} - x^*(t) \le \frac{1}{2}L \\ F * \sin (2\pi ((\tilde{x}-x^*(t)+\frac{1}{2}\alpha_2 L)/(1-\alpha_2)L) * \cos (\pi \tilde{y}/W), &  -\frac{1}{2}L \le \tilde{x}-x^*(t) \lt -\frac{1}{2}\alpha_2 L \\ 0, & - \frac{1}{2}\alpha_2 L \le \tilde{x} - x^*(t) \le \frac{1}{2}\alpha_1 L \end{array} \right.

The formula is calculated in the rectangle :math:`- L/2 \le \tilde{x} - x^*(t) \le L/2`  and  :math:`- W/2 \le \tilde{y} - y^*(t) \le R/2`, and zero outside this region.


To set up vessels in the model, see :ref:`section-shipwakes-setup`  


References
==========
Bayrakter, D., and S. Beji, (2013). "Numerical simulation of waves generated by a moving pressure field". *Ocean Engineering*, 59: 231-239. DOI: 10.1016/j.oceaneng.2012.12.025.

Daved, C.G., V. Roeber, N. Goseberg, and T. Schlurmann, (2017). "Generation and propagation of ship-borne waves - Solutions from a Boussinesq-type model". *Coastal Engineering*, 127: 170-187. DOI: 10.1016/j.coastaleng.2017.07.001.

Ertekin, R.C., Webster, W.C., Wehausen, J.V., 1986. "Waves caused by a moving disturbance in a shallow channel of finite width". Cambridge University Press, 169: 275-292. DOI: 10.1017/S0022112086000630.

Torsvik, T., Pederson, G., Dysthe, K., 2009. "Waves Generated by a Pressure Disturbance Moving in a Channel with Variable Cross-Sectional Topography". *J. of Waterway, Port, Coastal, and Ocean Eng.*, 135 (3). DOI: 10.1061/(ASCE)0733-950X(2009)135:3(120).

Wu, T.Y., 1987. "Generation of upstream advancing solitons by moving disturbances". Cambridge University Press, 184: 75-99. DOI: 10.1017/S0022112087002817.

