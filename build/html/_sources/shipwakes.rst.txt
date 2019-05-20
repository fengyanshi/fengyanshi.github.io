Ship-wake Module 
******************

We have implemented various types of source functions for ship-wave generation. 
 
1) **PRESSURE SOURCE TYPE I**

Following Ertekin et al. (1986), Wu (1987) and Torsvik et al. (2008), the pressure disturbance with a center point at :math:`(x^*, y^*`) is given by

.. math:: p_a(\tilde{x},\tilde{y},t) = P f(\tilde{x},t) q(\tilde{y},t),

where

.. math:: f(\tilde{x},t) = \left \{ \begin{array}{rl} \cos^2\left [\frac{\pi(\tilde{x}-x^*(t)-\frac{1}{2}\alpha_1 L)}{(1-\alpha_1) L} \right ], & \frac{1}{2}\alpha_1 L < \tilde{x} - x^*(t) \le \frac{1}{2}L \\ \cos^2\left [\frac{\pi(x^*(t)-\tilde{x}-\frac{1}{2}\alpha_2 L)}{(1-\alpha_2) L} \right ], & -\frac{1}{2}L \le \tilde{x}-x^*(t) \lt -\frac{1}{2}\alpha_2 L \\1, &  - \frac{1}{2}\alpha_2 L \le \tilde{x} - x^*(t) \le \frac{1}{2}\alpha_1 L \end{array} \right.

.. math:: q(\tilde{y},t) = \left \{ \begin{array}{rl} \cos^2 \left [\frac{\pi(|\tilde{y}-y^*(t)|-\frac{1}{2}\beta R)}{(1-\beta) R} \right ], & \frac{1}{2}\beta R < |\tilde{y} - y^*(t)| \le \frac{1}{2}R \\ 1, &  |\tilde{y} - y^*(t)| \le \frac{1}{2}\beta R \end{array} \right.

on the rectangle :math:`- L/2 \le \tilde{x} - x^*(t) \le L/2`  and  :math:`- R/2 \le \tilde{y} - y^*(t) \le R/2`, and zero outside this region, :math:`L` and :math:`R` represent the length and width of the pressure source, respectively. :math:`\alpha_2`, :math:`\alpha_1` and :math:`\beta` are parameters representing the shape of the draft region and :math:`0\le(\alpha_1,, \alpha_2, \beta)<1`. They can be evaluated using the block coefficient of  a watercraft as described below.  (:math:`\tilde{x}, \tilde{y}`) is the coordinate system for the pressure disturbance which may be rotated by an angle relative to the Boussinesq coordinate system (:math:`x,y`). :math:`P` is a parameter controlling the surface displacement. In fact, :math:`p_a` is the static depression around the vessel.  

In contrast to the formulation of the pressure distribution in the previous study such as Torsvik et al. (2008),  :math:`P` has a unit of meters and can be interpreted as the inverse barometer effect corresponding to the static surface depression for a stationary vessel. 

The values of :math:`\alpha_1`, :math:`\alpha_2`, and :math:`\beta` are shape parameters and can be obtained by adjusting :math:`\alpha_1`, :math:`\alpha_1` and :math:`\beta` to get the displaced volume (static submerged volume of the vessel)

.. math:: V_{\mbox{sub}} = \iint p_a d\tilde{x} d\tilde{y}

which should match a given block coefficient :math:`C_B` defined by 

.. math:: C_B = \frac{V_{\mbox{sub}} }{L \cdot R \cdot D}

in which :math:`D` represents draft of a vessel. 

2) **PRESSURE SOURCE TYPE II**

Type II of the pressure-type source is formulated following Bayrakter and Beji (2013). David et al. (2017) used this formulation in their tests. The pressure source can be written as

.. math:: p_a(\tilde{x},\tilde{y},t) = P \left[1-C_L(\tilde{x}/L)^4  \right] \left[1-C_B(\tilde{y}/W)^2  \right] e^{-a(\tilde{y}/W)^2}

where :math:`a`, :math:`C_L` and :math:`C_B` are form parameters. For a slender body, :math:`a=16.0`, :math:`C_L=2.0` and :math:`C_B=16.0`.  

3) **SLENDER SOURCE TYPE I**

For the slender-type source, the aditional volume flux induced by ship motion is applied in the mass conservation equation. 

.. Math:: dQ = P * \sin (\pi (\tilde{x}-x^*(t)/L) * \cos (\pi (\tilde{y}-y^*(t))/W)

where :math:`dQ` represents the flux gradient. 

4) **SLENDER SOURCE TYPE II**

The Type II of the slender source is similar to the Type I but with two additional parameters representing sizes of bow and stern. 
 
.. Math:: dQ = \left \{ \begin{array}{rl} P * \sin (2\pi ((\tilde{x}-x^*(t)-\frac{1}{2}\alpha_1 L)/(1-\alpha_1)L) * \cos (\pi \tilde{y}/W), &  \frac{1}{2}\alpha_1 L < \tilde{x} - x^*(t) \le \frac{1}{2}L \\ P * \sin (2\pi ((\tilde{x}-x^*(t)+\frac{1}{2}\alpha_2 L)/(1-\alpha_2)L) * \cos (\pi \tilde{y}/W), &  -\frac{1}{2}L \le \tilde{x}-x^*(t) \lt -\frac{1}{2}\alpha_2 L \\ 0, & - \frac{1}{2}\alpha_2 L \le \tilde{x} - x^*(t) \le \frac{1}{2}\alpha_1 L \end{array} \right.


To set up vessels in the model, see :ref:`section-shipwakes-setup`  

