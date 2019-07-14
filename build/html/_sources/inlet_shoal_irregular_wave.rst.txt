Irregular wave 
################

.. figure:: images/simple_cases/eta_inlet_shoal_irr.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

**input.txt is the same as the baseline case (regular wave) except:**

  `(Baseline case) <inlet_shoal_regular_wave.html>`_

|  **Add wavemaker**
|   WAVEMAKER = WK_IRR
|   DEP_WK = 10.0
|   Xc_WK = 250.0
|   Yc_WK = 0.0
|   Ywidth_WK = 20000.0
|   FreqPeak = 0.0893
|   FreqMin = 0.03
|   FreqMax = 0.3
|   Hmo = 1.00
|   GammaTMA = 3.3
|   ThetaPeak = 0.0
|   Sigma_Theta = 10.0

   Default option: EqualEnergy (refer to :ref:`info_equal_energy`)

|  **Add periodic boundary condition**
|   PERIODIC = T (refer to :ref:`info_periodic`)


