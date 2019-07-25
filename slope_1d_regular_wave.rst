.. _section-1d-reg:

Regular wave 
############

.. figure:: images/simple_cases/eta_1d_reg.jpg
    :width: 600px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

The following section will be modified in "input.txt" for this case. All other sections are defined in :ref:`section-1d-basics` for this example.
 
 Add a monochromatic wavemaker in a water depth of 10.0 m located 250.0 m from the left boundary that produces regular waves with amplitude 0.5 m and period 12.0 s:

  .. code-block:: rest

        !-----WAVEMAKER-----
          WAVEMAKER = WK_REG
          DEP_WK = 10.0 
          Xc_WK = 250.0 
          Yc_WK = 0.0 
          Tperiod = 12.0 
          AMP_WK = 0.5 
          Delta_WK = 3.0  ! the default is 0.5, set a larger number for nonlinear waves

 (refer to :ref:`definition_wavemaker` for parameter definitions)


