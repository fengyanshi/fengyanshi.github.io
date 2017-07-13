30 deg irregular waves, a submerged breakwater with partial reflection
#######################################################################

.. figure:: images/simple_cases/eta_inlet_shoal_irr_30deg_brk_abs.jpg
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
|   ThetaPeak = 30.0
|   Sigma_Theta = 10.0

|  **Add periodic boundary condition**
|   PERIODIC = T

|  **Add BREAKWATER FILE for partial reflection**
|   BREAKWATER_FILE = brk_shoal_inlet.txt
|   *brk_shoal_inlet.txt* has the same format as depth file, the numbers represent damping width (like sponge layer).

|  **Replace dep_shoal_inlet.txt with dep_shoal_inlet_brk.txt**
|   DEPTH_FILE = dep_shoal_inlet_brk.txt


