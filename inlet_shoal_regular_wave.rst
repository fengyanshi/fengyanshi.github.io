.. _section-inlet-reg:

Regular wave (baseline case)
############################

.. figure:: images/simple_cases/eta_inlet_shoal_reg.jpg
    :width: 500px
    :align: center
    :height: 300px
    :alt: alternate text
    :figclass: align-center

Update the title and wavemaker sections of "input.txt" for this example. The domain setup was defined in :ref:`section-inlet-basics`.

 Set a descriptive title for your simulation:

 .. code-block:: rest

        !-----TITLE-----
         TITLE = inlet_reg

 Add a monochromatic wavemaker located 250.0 m from the left boundary that produces a wave of amplitude 1.0 m and period 12.0 s:

 .. code-block:: rest

        !-----WAVEMAKER-----
         WAVEMAKER = WK_REG
         DEP_WK = 10.0 
         Xc_WK = 250.0 
         Yc_WK = 0.0 
         Tperiod = 12.0 
         AMP_WK = 1.0 
         Theta_WK = 0.0 

 (refer to :ref:`definition_wavemaker` for parameter definitions)


