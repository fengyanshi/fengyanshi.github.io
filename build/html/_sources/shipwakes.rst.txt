Ship-wake Module 
******************

Following Ertekin et al. (1986), Wu (1987) and Torsvik et al. (2008), the pressure disturbance with a center point at :math:`(x^*, y^*`) is given by

.. math:: p_a(\tilde{x},\tilde{y},t) = P f(\tilde{x},t) q(\tilde{y},t),

where

.. math:: f(\tilde{x},t) = \left \{ \begin{array}{rl} \cos^2\left [\frac{\pi(|\tilde{x}-x^*(t)|-\frac{1}{2}\alpha L)}{(1-\alpha) L} \right ], & \frac{1}{2}\alpha L < |\tilde{x} - x^*(t)| \le \frac{1}{2}L \\ 1, &  |\tilde{x} - x^*(t)| \le \frac{1}{2}\alpha L \end{array} \right.

.. math:: q(\tilde{y},t) = \left \{ \begin{array}{rl} \cos^2 \left [\frac{\pi(|\tilde{y}-y^*(t)|-\frac{1}{2}\beta R)}{(1-\beta) R} \right ], & \frac{1}{2}\beta R < |\tilde{y} - y^*(t)| \le \frac{1}{2}R \\ 1, &  |\tilde{y} - y^*(t)| \le \frac{1}{2}\beta R \end{array} \right.

on the rectangle :math:`- L/2 \le \tilde{x} - x^*(t) \le L/2 $ and $ - R/2 \le \tilde{y} - y^*(t) \le R/2`, and zero outside this region, :math:`L` and :math:`R` represent the length and width of the pressure source, respectively. :math:`\alpha` and :math:`\beta` are parameters representing the shape of the draft region and :math:`0\le(\alpha,\beta)<1`. They can be evaluated using the block coefficient of  a watercraft as described below.  (:math:`\tilde{x}, \tilde{y}`) is the coordinate system for the pressure disturbance which may be rotated by an angle relative to the Boussinesq coordinate system (:math:`x,y`). :math:`P` is a parameter controlling the surface displacement. In fact, :math:`p_a` is the static depression around the vessel.  

In contrast to the formulation of the pressure distribution in the previous study such as Torsvik et al. (2008),  :math:`P` has a unit of meters and can be interpreted as the inverse barometer effect corresponding to the static surface depression for a stationary vessel. 

The values of :math:`\alpha` and :math:`\beta` are shape parameters and can be obtained by adjusting :math:`\alpha` and :math:`\beta` to get the displaced volume (static submerged volume of the vessel)

.. math:: V_{\mbox{sub}} = \iint p_a d\tilde{x} d\tilde{y}

which should match a given block coefficient :math:`C_B` defined by 

.. math:: C_B = \frac{V_{\mbox{sub}} }{L \cdot R \cdot D}

in which :math:`D` represents draft of a vessel. 

To set up vessels in the model, see :ref:`section-shipwakes-setup`  
