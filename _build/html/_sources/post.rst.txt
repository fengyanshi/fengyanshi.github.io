.. _section_post:

Post Processing
*****************
* Wave height calculation


For spectral wave simulations, both average wave height and root-mean-square wave height are calculated using zero-crossing at each grid point. Significant wave height is evaluated using Goda's (2000) formula

.. math:: H_{1/3} = 4.004\sqrt{m_0}

where

.. math:: m_0 = \frac{1}{t_2-t_1} \int^{t_2}_{t_1} \eta^2 dt
