Regular wave 30 deg oblique incidence
######################################

.. figure:: images/simple_cases/eta_inlet_shoal_reg_30deg.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

**input.txt is the same as the baseline case (regular wave) except:**

  `(Baseline case) <inlet_shoal_regular_wave.html>`_

|  **Wavemaker** 
|   WAVEMAKER = WK_REG
|   DEP_WK = 10.0 
|   Xc_WK = 250.0 
|   Yc_WK = 0.0 
|   Tperiod = 12.0 
|   AMP_WK = 1.0 
|   *Theta_WK = 30.0*

|  **Add periodic boundary condition**
|   PERIODIC = T

